---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "queuing"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/queuing.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Queuing

A queue retains calls and runs them according to FIFO, LIFO, or priority order with configurable concurrency and wait. Async queues can retry, abort, expire, start, and stop items while exposing observable state.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Choose ordering and concurrency from workload semantics.
- Give priority values a stable documented meaning.
- Set expiration and retry limits for work that can become stale.
- Stop accepting or drain work deliberately during unmount or shutdown.

## Constraints and failure modes

- LIFO can starve older work during a sustained burst.
- Priority queues can starve low-priority items without policy.
- Retries multiply load and must be bounded.
- Stopping a queue does not imply every running task was cancelled; propagate abort where required.

## Retrieval cues

Use this page when work mentions queuing, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/queuing.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/async-queuing.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/reference/classes/AsyncQueuer.md

