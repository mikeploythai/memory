---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "rate limiting"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/rate-limiting.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# Rate limiting

Rate limiting caps executions within a time window. Fixed and sliding windows have different boundary behavior. Async variants add settlement, error, retry, and abort handling. Server use may persist state so multiple requests or reloads share the same allowance.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Select fixed or sliding windows according to the quota contract.
- Key server limits by the intended subject and action, not a raw unvalidated client string.
- Persist state only in a store whose clock and serialization meet the documented contract.
- Expose rejection or remaining allowance when callers need to retry safely.

## Constraints and failure modes

- Fixed windows permit boundary bursts.
- Client-only state cannot enforce a security or billing quota.
- Multiple server instances need shared state for a global limit.
- Clock skew, stale persistence, or key collisions can grant or deny the wrong allowance.

## Retrieval cues

Use this page when work mentions rate limiting, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/rate-limiting.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/async-rate-limiting.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/guides/server-rate-limiting.md

