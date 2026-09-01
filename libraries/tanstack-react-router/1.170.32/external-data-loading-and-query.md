---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "external data loading and TanStack Query integration"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/external-data-loading.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# External data loading and TanStack Query integration

External caches work best when the route loader coordinates fetching and the cache owns the data lifecycle. Put the Query client in router context, define stable query options outside the route component, and have the loader call `ensureQueryData` or the appropriate prefetch operation. The component can then use the same query options. This starts work at navigation time while retaining Query's cache, mutation, retry, and observation behavior.

The route's `loaderDeps` must contain every URL-derived value used in the query key. The query key must contain every variable used by the query function. These two dependency declarations serve different caches but must describe the same data identity. A missing value can show data for another route or prevent a loader from rerunning when search state changes.

Avoid duplicate ownership. If Query determines staleness, configure Router's preload stale time so Router does not independently keep settled preload data fresh. Router can still coordinate navigation and share in-flight work, while Query decides whether cached data is usable. Do not fetch once in a loader and again with a different key in the component.

Errors and redirects should cross the route boundary intentionally. Query errors used during a loader can reach the route error component. Authentication redirects generally belong in `beforeLoad`, before a protected query begins. After mutations, invalidate or update the exact Query keys; invalidate the router only when route-owned loader state also changed.

For SSR, create request-scoped clients on the server rather than sharing a singleton across users, dehydrate only the intended cache state, and hydrate it on the client before query consumers expect it.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/external-data-loading.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/integrations/query.md


