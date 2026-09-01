---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "persistence, devtools, and api map"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/devtools.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Persistence, devtools, and API map

Pacer utilities expose observable stores and devtools integration so execution, pending work, errors, and status can be inspected. Selected utilities can persist queue or rate-limit state. The generated references separate core classes, functions, options, state, and React hooks.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Mount devtools only in intended environments and avoid exposing sensitive arguments.
- Persist only serializable state with a stable key and version.
- Read the grouped class, options, and state pages together for the chosen utility.
- Use subscriptions for external observation without forcing unrelated React renders.

## Constraints and failure modes

- Persisted timing state depends on a coherent clock and can become stale.
- Changing serialization or keys without migration can reset or corrupt allowance and queue state.
- Devtools payloads may contain function arguments or errors with user data.
- Subscribing without cleanup leaks observers and duplicate work.

## Retrieval cues

Use this page when work mentions persistence, devtools, and api map, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/devtools.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/reference/index.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/framework/react/reference/index.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/examples/react/useAsyncRateLimiterWithPersister/README.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/examples/react/useQueuerWithPersister/README.md

