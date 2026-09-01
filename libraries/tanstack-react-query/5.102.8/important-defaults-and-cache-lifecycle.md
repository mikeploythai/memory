---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "important defaults and query cache lifecycle"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/important-defaults.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Important defaults and query cache lifecycle

TanStack Query starts with aggressive freshness defaults. Cached query data is stale immediately unless `staleTime` says otherwise. Stale queries can refetch when a new observer mounts, the window regains focus, or the network reconnects. These events do not mean the cache was discarded; they mean stale data can be shown while a background request refreshes it.

Inactive queries remain cached after their last observer unmounts and are garbage-collected after `gcTime`, five minutes by default. `staleTime` and `gcTime` are independent: one controls whether data should refresh, the other controls how long unused data can remain. Setting a long `staleTime` does not retain an inactive query forever, and increasing `gcTime` does not make old data fresh.

Failed queries retry three times by default with backoff before surfacing an error. Structural sharing keeps stable references when JSON-compatible result subtrees have not changed, which supports memoization and reduces renders. Non-JSON values may always appear changed unless custom behavior is configured.

Choose defaults at the `QueryClient` level only when they apply broadly. Override them per query for data with different volatility or cost. Do not disable focus refetching or retries globally merely to hide a noisy endpoint; first decide whether the query key, stale time, error handling, or request semantics are wrong.

A query's lifecycle follows its observers and key, not the component that first fetched it. Multiple components using the same key share the same cached result and in-flight request. Treat the key as data identity and keep its query function compatible everywhere it is used.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/important-defaults.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/caching.md


