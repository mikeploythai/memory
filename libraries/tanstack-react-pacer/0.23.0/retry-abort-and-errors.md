---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "retry, abort, and error handling"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/async-retrying.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Retry, abort, and error handling

Async Pacer utilities share lifecycle concerns: success, error, settlement, retry, and abort. `AsyncRetryer` isolates retry policy, while async debounce, throttle, rate limit, queue, and batch utilities integrate retries with their timing or pressure semantics.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Bound attempts and choose delay/backoff based on the failing service.
- Retry only errors classified as transient.
- Propagate the provided abort signal into fetches or other cancellable work.
- Use settled callbacks for cleanup that must run after either success or failure.

## Constraints and failure modes

- Retrying validation, authorization, or deterministic failures wastes capacity.
- Aborting a wrapper without passing its signal to the underlying operation does not stop that operation.
- Retries inside a queue or rate limiter still consume time and may affect concurrency or allowance.
- Callback exceptions need their own handling; they can obscure the original failure.

## Retrieval cues

Use this page when work mentions retry, abort, and error handling, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/async-retrying.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/reference/classes/AsyncRetryer.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/reference/interfaces/AsyncRetryerOptions.md

