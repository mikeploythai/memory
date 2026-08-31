---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "debounce React input"
source: "https://tanstack.com/pacer/latest/docs/framework/react/adapter"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0; @tanstack/pacer@0.22.0; beta"
---

# Debounce React input with TanStack Pacer

TanStack Pacer provides debouncing, throttling, rate limiting, queuing, and batching. The React adapter re-exports the framework-neutral core. Version 0.23.0 is beta software.

## Installation

```sh
npm install @tanstack/react-pacer
```

## Debounce an input

```tsx
import { useDebouncer } from '@tanstack/react-pacer'

export function Search() {
  const debouncer = useDebouncer(
    (query: string) => fetch('/api/search?q=' + encodeURIComponent(query)),
    { wait: 500 },
    (state) => ({ isPending: state.isPending }),
  )

  return (
    <>
      <input onChange={(event) => debouncer.maybeExecute(event.target.value)} />
      {debouncer.state.isPending ? <span>Waiting…</span> : null}
    </>
  )
}
```

The selector makes `isPending` reactive. Without a selector, the hook's reactive `state` object is empty.

## Notes

- Choose debouncing, throttling, rate limiting, queueing, or batching according to whether delayed work should be replaced, spaced, limited, preserved, or grouped.
- Use async utilities when Pacer must track settlement, errors, retries, cancellation, or concurrency. An async callback passed to a synchronous utility does not add those behaviors.
- Pin the React adapter and resolved core package independently because their versions can differ.
- Beta APIs may change.

## Sources

- https://tanstack.com/pacer/latest/docs/overview
- https://tanstack.com/pacer/latest/docs/installation
- https://tanstack.com/pacer/latest/docs/guides/which-pacer-utility-should-i-choose
- https://github.com/TanStack/pacer/releases
