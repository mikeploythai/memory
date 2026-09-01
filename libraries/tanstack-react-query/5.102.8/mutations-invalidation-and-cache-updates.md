---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "mutations, invalidation, and cache updates"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/mutations.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Mutations, invalidation, and cache updates

Mutations represent create, update, delete, and other side effects. `useMutation` tracks the latest mutation state and exposes `mutate` and `mutateAsync`. Lifecycle callbacks can run before the request, after success, after failure, and after settlement. Await returned promises from invalidation or related work when the mutation should remain pending until the cache is reconciled.

Invalidation is the simplest reliable follow-up when the server determines the canonical result. In a success callback, invalidate the resource keys affected by the mutation. Prefix filters can refresh a family of list and detail queries; exact filters avoid unrelated requests. Mutation variables and returned data are available to callbacks for choosing those keys.

When the server response already contains the complete updated entity, call `setQueryData` for its exact key. Cache updates must be immutable. Do not mutate the prior object and return it, because observers and structural sharing may retain references and skip updates. For partial responses, invalidation is safer than constructing a result the server did not provide.

Consecutive calls have callback-order considerations: hook-level handlers apply to every mutation, while per-call handlers are associated with an individual observer and may not run after unmount. Do not put essential cache consistency only in a component-local callback that can disappear.

Mutations do not automatically retry by default in the same way queries do. If retries are enabled, ensure the server operation is idempotent or protected against duplicate effects. Treat mutation errors as application outcomes and decide whether to retain form input, roll back optimistic state, or offer an explicit retry.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/mutations.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/invalidations-from-mutations.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/updates-from-mutation-responses.md


