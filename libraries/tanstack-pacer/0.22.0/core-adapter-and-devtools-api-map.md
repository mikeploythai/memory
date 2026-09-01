---
library: "@tanstack/pacer"
version: "0.22.0"
topic: "core adapter and devtools API map"
source: "https://github.com/TanStack/pacer/blob/c75895520669b08dc8946b42e1a6d529ca977230/docs/reference/index.md"
retrieved_at: "2026-08-31"
source_ref: "c75895520669b08dc8946b42e1a6d529ca977230"
---

# Core, adapter, and devtools API map

Use this map to retrieve the smallest relevant generated API page. Exact
signatures should come from the release-pinned source or matching generated
reference, not an assumption based on another package's version.

## Package versions

| Package | Version | Release ref |
|---|---:|---|
| `@tanstack/pacer` | `0.22.0` | `c758955` |
| `@tanstack/pacer-lite` | `0.2.2` | `a894009` |
| `@tanstack/react-pacer` | `0.23.0` | `c758955` |
| `@tanstack/preact-pacer` | `0.23.0` | `c758955` |
| `@tanstack/solid-pacer` | `0.22.0` | `c758955` |
| `@tanstack/angular-pacer` | `0.24.0` | `c758955` |
| `@tanstack/pacer-devtools` | `1.4.0` | `c758955` |
| React Pacer devtools | `0.8.0` | `c758955` |
| Preact and Solid Pacer devtools | `0.7.0` | `c758955` |

## Core utility families

Each utility has synchronous and asynchronous classes, options, state, and
functional helpers where applicable.

| Family | Core surface |
|---|---|
| Debounce | `Debouncer`, `AsyncDebouncer`, `debounce`, `asyncDebounce`, options/state |
| Throttle | `Throttler`, `AsyncThrottler`, `throttle`, `asyncThrottle`, options/state |
| Rate limit | `RateLimiter`, `AsyncRateLimiter`, `rateLimit`, `asyncRateLimit`, options/state |
| Queue | `Queuer`, `AsyncQueuer`, queue helpers, options/state, persistence-related APIs |
| Batch | `Batcher`, `AsyncBatcher`, `batch`, `asyncBatch`, options/state |

Generated index:
[Core API](https://tanstack.com/pacer/latest/docs/reference/index.md).

## Framework indexes

| Framework | Primary style | Reference |
|---|---|---|
| React | `use*` hooks, provider, selected state, `Subscribe` | [React API](https://tanstack.com/pacer/latest/docs/framework/react/reference/index.md) |
| Preact | `use*` hooks, provider, selected state, `Subscribe` | [Preact API](https://tanstack.com/pacer/latest/docs/framework/preact/reference/index.md) |
| Solid | `create*` primitives, provider, selected signals | [Solid API](https://tanstack.com/pacer/latest/docs/framework/solid/reference/index.md) |
| Angular | `inject*` APIs, signals, `providePacerOptions` | [Angular API](https://tanstack.com/pacer/latest/docs/framework/angular/reference/index.md) |

## Adapter API layers

Framework adapters expose several shapes around the same core utilities:

- instance APIs such as `useDebouncer` retain methods and selected state;
- callback APIs such as `useDebouncedCallback` return a callable function;
- state/signal APIs connect controlled execution to framework state;
- value APIs return a paced value;
- provider APIs define defaults for descendant instances;
- selector and `Subscribe` APIs opt into fine-grained reactive state.

Choose the narrowest API that still provides required lifecycle methods and
state. Use an instance API when the caller needs `cancel()`, `flush()`, queue
control, or direct state inspection.

## Devtools

A utility registers with devtools only when it has a `key`:

```ts
const debouncer = new Debouncer(fn, {
  key: 'Search Debouncer',
  wait: 500,
})
```

Default devtools imports become no-ops in production. The React plugin exposes
`@tanstack/react-pacer-devtools/production` for deliberate production
inclusion. Retrieve that adapter's versioned setup before implementation; this
core page only maps the package and registration requirement.

## Devtools gaps

Official devtools setup covers React and Solid. Angular is marked “Coming
soon.” The package inventory includes a Preact devtools adapter, but the
top-level devtools page does not document its setup.

## Sources

- [Official docs index](https://tanstack.com/pacer/latest/llms.txt)
- [Core API index](https://tanstack.com/pacer/latest/docs/reference/index.md)
- [React adapter](https://tanstack.com/pacer/latest/docs/framework/react/adapter.md)
- [Devtools](https://tanstack.com/pacer/latest/docs/devtools.md)
- [Release-pinned packages](https://github.com/TanStack/pacer/tree/c75895520669b08dc8946b42e1a6d529ca977230/packages)
- [Core release](https://github.com/TanStack/pacer/releases/tag/%40tanstack%2Fpacer%400.22.0)
