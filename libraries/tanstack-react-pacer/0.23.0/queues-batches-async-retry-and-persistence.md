---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "queues batches async retry and persistence"
source: "https://github.com/TanStack/pacer/blob/c75895520669b08dc8946b42e1a6d529ca977230/docs/guides/queuing.md"
retrieved_at: "2026-08-31"
source_ref: "c75895520669b08dc8946b42e1a6d529ca977230"
---

# Queues, batches, async retry, and persistence

This page inventories React adapter queue, batch, retry, and persistence APIs
at `0.23.0`. Use a queue when individual items must be retained and processed.
Use a batcher when several items should be delivered together to one function.

## Queuing

Pacer queues can order work and control processing pressure. The documented
feature set includes FIFO, LIFO, and priority behavior, configurable wait or
concurrency, start/stop control, and item expiration.

React async upload example:

```tsx
import { useAsyncQueuer } from '@tanstack/react-pacer'

function UploadInput() {
  const queuer = useAsyncQueuer(
    async (file: File) => {
      await uploadFile(file)
    },
    { concurrency: 3 },
  )

  return (
    <input
      type="file"
      multiple
      onChange={(event) => {
        const files = event.target.files
        if (!files) return
        Array.from(files).forEach((file) => queuer.addItem(file))
      }}
    />
  )
}
```

Unlike debouncing or throttling, a queue is intended for work that should not
be discarded merely because calls arrive quickly. Expiration, cancellation,
and error policy can still remove or halt work, so configure them explicitly.

## Async queue option helper

```ts
import { asyncQueuerOptions } from '@tanstack/react-pacer'

const commonQueueOptions = asyncQueuerOptions({
  concurrency: 3,
  addItemsTo: 'back',
})
```

The React adapter re-exports core APIs. Keeping the import on the adapter
package makes the package identity explicit for this page.

## Batching

A batcher accumulates items and invokes one function with a group. Official
guides cover time-based, size-based, whichever-first, and custom-condition
triggers.

Retrieve the pinned `Batcher` and `BatcherOptions` generated pages before
writing configuration. This inventory verified the available trigger concepts,
but did not verify every release-specific option name. Hosted `latest`
generated references may move ahead of `0.22.0`.

## Async batching

Use `AsyncBatcher` or framework async-batcher APIs when the batch function
returns a promise. Async state and callbacks distinguish pending execution,
success, failure, and settlement.

```tsx
import { useAsyncBatcher } from '@tanstack/react-pacer'

const batcher = useAsyncBatcher(
  async (items: Array<string>) => {
    await sendBatch(items)
  },
  { wait: 1000 },
)
```

## Retry and abort

The async guides include a separate retrying guide for vanilla, React,
Preact, Solid, and Angular. Async utilities support error/success/settled
handling, and the product overview describes retry and abort support.

Before implementing retries, decide:

- which failures are retryable;
- maximum attempts and timing;
- whether a queued or batched item remains ordered after retry;
- how cancellation propagates;
- whether callbacks may create duplicate side effects.

The official docs do not provide a cross-utility idempotency policy. The
controlled function remains responsible for safe repeated execution.

## Persistence

Rate limiters and queues have persistence-oriented APIs and examples, including
`useRateLimiterWithPersister` and `useQueuerWithPersister` in React and Preact,
with corresponding Angular injection examples.

Persistence can preserve execution-window or queue state across reloads. It
does not turn browser storage into a shared server-side quota or durable job
system. Validate serialization, expiration, and version migration in the host
application.

## State subscriptions

Framework adapters expose selected reactive state and `Subscribe` helpers.
For example, subscribe only to queue size when that is all the UI renders:

```tsx
<queuer.Subscribe selector={(state) => ({ size: state.size })}>
  {({ size }) => <span>Queue size: {size}</span>}
</queuer.Subscribe>
```

## Gaps

- No official durable-storage schema or cross-version migration contract.
- No server-distributed queue or rate-limit guarantee.
- No general troubleshooting section for stuck or repeatedly failing work.
- Breaking queue/batcher changes are recorded in changelogs rather than a
  migration guide.

## Sources

- [Vanilla queuing](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/queuing.md)
- [Vanilla batching](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/batching.md)
- [Vanilla async queuing](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/async-queuing.md)
- [Vanilla async batching](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/async-batching.md)
- [Vanilla async retrying](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/async-retrying.md)
- [React adapter](https://tanstack.com/pacer/latest/docs/framework/react/adapter.md)
- [Release repository](https://github.com/TanStack/pacer/tree/c75895520669b08dc8946b42e1a6d529ca977230)

