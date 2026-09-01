---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "batching"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/batching.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Batching

A batcher collects items and invokes one function with a group. A batch can trigger by size, time, whichever happens first, or a custom condition. Async batching observes the grouped promise and exposes success, error, settlement, retry, and abort behavior.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Choose a maximum batch size and maximum wait so neither memory nor latency is unbounded.
- Preserve item identity when mapping a grouped result back to callers.
- Flush deliberately at lifecycle boundaries when dropping the pending batch would lose work.
- Make the batch operation idempotent when retries are enabled.

## Constraints and failure modes

- A size-only trigger may never flush low traffic.
- A time-only trigger can create oversized batches during bursts.
- One malformed item can fail an entire batch unless the service and mapping define partial failure.
- Retrying a non-idempotent batch can duplicate successful work.

## Retrieval cues

Use this page when work mentions batching, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/batching.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/async-batching.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/reference/classes/AsyncBatcher.md

