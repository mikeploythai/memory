---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "debouncing"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/debouncing.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Debouncing

A debouncer delays execution until calls stop for the configured wait. Trailing execution keeps the latest arguments; leading execution can run at the start of a burst. Async debouncing adds promise settlement, error callbacks, cancellation, abort support, and retry behavior.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Choose leading and trailing behavior explicitly.
- Cancel pending work on scope changes when its result would be stale.
- Use the React callback hook for event handlers, value/state helpers for derived UI, and the instance hook when controls or state are needed.
- For async search, associate results with the active request or abort superseded work.

## Constraints and failure modes

- A trailing debounce may never run during a continuous stream.
- Leading plus trailing can execute twice for one burst when configured to do so.
- Debouncing a recreated callback/options object can reset timing every render.
- Cancelling a timer does not necessarily cancel underlying async work unless an abort signal reaches it.

## Retrieval cues

Use this page when work mentions debouncing, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/debouncing.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/async-debouncing.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/framework/react/adapter.md

