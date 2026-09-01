---
library: "@tanstack/pacer"
version: "0.22.0"
topic: "debounce throttle and rate limit"
source: "https://github.com/TanStack/pacer/blob/c75895520669b08dc8946b42e1a6d529ca977230/docs/guides/which-pacer-utility-should-i-choose.md"
retrieved_at: "2026-08-31"
source_ref: "c75895520669b08dc8946b42e1a6d529ca977230"
---

# Debounce, throttle, and rate limit

These utilities all reduce execution pressure, but they preserve different
work. Choose based on what may be discarded or rejected.

## Decision table

| Requirement | Utility |
|---|---|
| Keep only the latest call after activity becomes quiet | Debouncer |
| Sample work at a controlled interval | Throttler |
| Enforce a quota in a time window | Rate limiter |

Use a queue when every item must eventually run, and a batcher when multiple
items should be processed together.

## Debouncing

A debouncer delays execution until calls stop for the configured wait period.
Earlier calls are discarded in favor of the latest arguments.

```ts
import { Debouncer } from '@tanstack/pacer'

const search = new Debouncer(
  (query: string) => fetchSearchResults(query),
  {
    wait: 500,
    leading: false,
    trailing: true,
  },
)

search.maybeExecute('tanstack')
```

Use `cancel()` to discard pending work and `flush()` to trigger pending work
immediately. Leading and trailing options determine whether execution occurs at
the start or end of the wait window.

## Throttling

A throttler limits how often a function executes while calls continue. It is a
fit for high-frequency UI events where intermediate work may be dropped.

```ts
import { Throttler } from '@tanstack/pacer'

const updatePointer = new Throttler(
  (position: { x: number; y: number }) => renderPointer(position),
  {
    wait: 100,
    leading: true,
    trailing: true,
  },
)

window.addEventListener('pointermove', (event) => {
  updatePointer.maybeExecute({ x: event.clientX, y: event.clientY })
})
```

The example applies documented API shapes to a pointer event. The official
docs do not prescribe this exact application wiring.

## Rate limiting

A rate limiter accepts calls until a configured quota is reached. Additional
calls are rejected until capacity returns.

The guides document fixed and sliding windows. Rate limiting is client-side
unless the chosen execution environment provides shared authoritative state;
do not use a browser-only limiter as a server security boundary.

Retrieve the release-pinned `RateLimiter` and `RateLimiterOptions` references
before implementation. This page verifies the policy distinction, not every
`0.22.0` constructor option.

## Async variants

Use `AsyncDebouncer`, `AsyncThrottler`, or `AsyncRateLimiter` and their helper
functions/hooks for promise-returning work. Async variants provide lifecycle
for resolved results and error handling. Consult the exact API page for retry
and abort options before implementation.

## Reactive state

Core utilities expose store-backed state. Framework adapters add their own
reactive selection APIs; those APIs must be indexed under the adapter package
before implementation.

## Failure modes

- Debouncing is wrong when every call must execute.
- Throttling can drop intermediate calls.
- Rate limiting rejects excess calls; it does not queue them automatically.
- Async work may require abort or stale-result handling beyond timing control.
- Persistence behavior must be chosen deliberately for rate limits that should
  survive reloads.

## Sources

- [Utility selection guide](https://tanstack.com/pacer/latest/docs/guides/which-pacer-utility-should-i-choose.md)
- [Vanilla debouncing](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/debouncing.md)
- [Vanilla throttling](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/throttling.md)
- [Vanilla rate limiting](https://tanstack.com/pacer/latest/docs/framework/vanilla/guides/rate-limiting.md)
- [Release repository](https://github.com/TanStack/pacer/tree/c75895520669b08dc8946b42e1a6d529ca977230)
