---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "throttling"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/throttling.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Throttling

A throttler limits how frequently a function executes while calls continue. Leading and trailing options determine which edge of an interval runs. Async throttling tracks settlement and errors while still enforcing the cadence.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Use throttling when a regular sample is acceptable and intermediate values may be discarded.
- Choose interval and edge behavior from the UI or service requirement.
- Keep the wrapped callback stable in React.
- Use instance state when the UI needs pending, execution count, or manual controls.

## Constraints and failure modes

- Throttle is not a guarantee that every call runs.
- A trailing call can apply stale data after the owning component or selection changes.
- Long async work can overlap unless the chosen async options constrain it.
- Intervals shorter than the real work duration do not increase completion capacity.

## Retrieval cues

Use this page when work mentions throttling, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/throttling.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/async-throttling.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/framework/react/adapter.md

