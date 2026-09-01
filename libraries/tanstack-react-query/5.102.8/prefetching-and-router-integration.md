---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "prefetching and router integration"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/prefetching.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Prefetching and router integration

Prefetching moves a query request before the component that consumes it. Use `prefetchQuery` when the result can remain in the cache without being returned to the caller, and `ensureQueryData` when code needs a cached or fetched value. Both should use the same key, function, and stale-time options as the eventual hook; a shared `queryOptions` definition keeps them aligned.

A router loader is a natural prefetch boundary because it knows the destination before rendering. Derive the query key from typed route params and validated search state, then ensure or prefetch it in the loader. The component observes the same key with `useQuery`. This prevents the component tree from discovering the request late and reduces route-level waterfalls.

Prefetch only when intent is credible. Hover, focus, viewport, or known next-page actions are common triggers. A prefetch that is never observed is garbage-collected under the normal inactive-query policy. Set an appropriate stale time; otherwise prefetched data is immediately stale and may refetch when the component mounts.

For TanStack Router, let Query own query freshness and configure Router's loader/preload freshness to avoid two caches independently suppressing work. Put the request-scoped Query client in router context. On the server, never share one client across users.

`prefetchInfiniteQuery` uses the infinite-query contract, including `initialPageParam`, and normally prefetches the first page unless more pages are requested deliberately. Do not populate an infinite key with ordinary query data.

Prefetch errors are not normally thrown to the prefetch caller. If navigation must fail on missing data, use an ensuring/fetching operation whose error behavior matches the loader boundary.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/prefetching.md
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/examples/react/prefetching
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/integrations/query.md


