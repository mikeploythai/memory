---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "queries, keys, functions, and invalidation"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/queries.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Queries, keys, functions, and invalidation

A query describes asynchronous data with a unique key and a function that returns a promise. The key must be an array at the top level and should include every variable used by the query function. Keys are deterministically hashed, so object property order does not change identity, while array item order does. Use serializable key parts and do not reuse one key for different result shapes such as a normal query and an infinite query.

The query function should either resolve data or throw an error. An HTTP client that resolves non-success responses must be checked explicitly. TanStack Query supplies an `AbortSignal` through the query-function context; pass it to fetch or another cancellable client so obsolete work can be cancelled.

Query options can be colocated in a reusable `queryOptions` helper. This preserves the relationship among a key, function, and options for hooks, prefetching, and imperative cache access. Centralized key factories can help large applications, but the keys still need to expose the variables that determine the resource.

Invalidation marks matching queries stale and refetches active matches according to the invalidation filters. It does not require normalized-cache mutation. Match by exact key when only one query is affected, or by a meaningful prefix when a whole resource family changed. Broad invalidation is safe but can cause unnecessary requests.

Invalidation is often the right mutation follow-up when the server is the source of truth. If the mutation response already contains the canonical updated object, update the matching cache immutably instead. Do not mutate cached objects in place; structural sharing and observers depend on replacement values to detect changes.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/queries.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/query-keys.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/query-functions.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/query-invalidation.md


