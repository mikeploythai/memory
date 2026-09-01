---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "choosing a timing policy"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/which-pacer-utility-should-i-choose.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Choosing a timing policy

Pacer offers five distinct pressure policies. Debounce keeps the latest call after quiet; throttle samples at a bounded cadence; rate limiting enforces an allowance; queueing keeps every task and controls order/concurrency; batching keeps every item but groups execution. The choice starts with what may be dropped, delayed, rejected, reordered, or grouped.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Write down the product policy before choosing an API.
- Use debounce for superseded input, throttle for sampled updates, rate limiting for quotas, queues for retained work, and batches for grouped work.
- Choose sync or async variants based on whether completion, error, retry, or cancellation must be observed.
- Expose pending and execution state when it affects user expectations.

## Constraints and failure modes

- Debounce drops earlier calls; it is wrong when every task must run.
- Throttle drops intermediate calls; it is not a concurrency queue.
- Rate limiting may reject excess work unless the application handles it.
- Batching changes execution granularity and queueing changes latency.

## Retrieval cues

Use this page when work mentions choosing a timing policy, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/which-pacer-utility-should-i-choose.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/overview.md

