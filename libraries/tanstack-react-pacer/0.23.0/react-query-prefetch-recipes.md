---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "react query prefetch recipes"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/examples/react/react-query-debounced-prefetch/README.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# React Query prefetch recipes

The exact release includes examples that debounce, throttle, or queue TanStack Query prefetch work. They demonstrate that timing policy belongs around the prefetch trigger while Query continues to own cache identity, request deduplication, and freshness.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Debounce speculative prefetch when only the final hovered or typed target matters.
- Throttle when regular sampling is acceptable during rapid navigation.
- Queue when every requested prefetch must eventually run, and bound concurrency.
- Use stable query keys and pass cancellation into the query function when supported.

## Constraints and failure modes

- Debouncing can skip intermediate destinations entirely.
- Throttling may prefetch an earlier target and drop the final target unless trailing behavior is configured.
- Queueing stale prefetches can waste bandwidth after navigation intent changes.
- Pacer does not replace Query cache freshness, deduplication, or error policy.

## Retrieval cues

Use this page when work mentions react query prefetch recipes, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/examples/react/react-query-debounced-prefetch/README.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/examples/react/react-query-throttled-prefetch/README.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/examples/react/react-query-queued-prefetch/README.md

