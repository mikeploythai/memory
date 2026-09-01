---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "route data loading, cache, and revalidation"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/data-loading.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Route data loading, cache, and revalidation

Route loaders start before rendering and can run in parallel across a matched branch. A loader receives typed params, validated search-derived dependencies, route context, location, preload state, and an abort controller. Components consume the resolved value through the route's `useLoaderData` API. Deep components can use `getRouteApi` to avoid importing a route module and creating a circular dependency.

The built-in cache is keyed by the parsed pathname plus the object returned by `loaderDeps`. Put every search value or other input that changes the result into `loaderDeps`; omitting a dependency can reuse data for the wrong state. `staleTime` controls freshness, `gcTime` controls retention of unused entries, and `shouldReload` can suppress reloads. These settings solve different problems: an infinite stale time prevents staleness, while a blocking stale reload still permits staleness but waits for refreshed data.

Pass `abortController.signal` to cancellable I/O. Preloads and navigations can share in-flight loader work, so cancellation occurs only when an invocation is obsolete and no consumer still needs it. Code that ignores the signal may finish unnecessary work and can race with newer navigation.

Use the Router cache for route-scoped data when its lifecycle is sufficient. For normalized data, mutations, cross-route reuse, persistence, or more elaborate cache policies, integrate an external cache. Avoid running two independent freshness systems with conflicting stale times. When a mutation changes loader-backed data, call router invalidation or update the external cache intentionally; returning from an action does not automatically make every related loader fresh.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/data-loading.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/data-mutations.md


