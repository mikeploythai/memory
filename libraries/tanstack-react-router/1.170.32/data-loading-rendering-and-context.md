---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "data loading, rendering, and context"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/data-loading.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Data loading, rendering, and context

Route loading follows the matched route tree. `beforeLoad` can add context or
stop navigation, `loaderDeps` describes search-derived dependencies, and
`loader` resolves route data. Components consume the result through route APIs.

## Loader example

```tsx
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/posts/$postId')({
  loader: ({ params, abortController }) =>
    fetch(`/api/posts/${params.postId}`, {
      signal: abortController.signal,
    }).then((response) => response.json()),
  component: Post,
})

function Post() {
  const post = Route.useLoaderData()
  return <h1>{post.title}</h1>
}
```

The Router cache is a lightweight stale-while-revalidate cache. Configure
staleness, preload staleness, and garbage-collection timing deliberately.
Preloading starts work before navigation and should not silently compete with
an external cache.

## Router context

Declare required root context with `createRootRouteWithContext`, then provide
the value to `createRouter`.

```tsx
import {
  createRootRouteWithContext,
  createRouter,
} from '@tanstack/react-router'

type RouterContext = {
  auth: { userId?: string }
}

export const rootRoute = createRootRouteWithContext<RouterContext>()({})

const router = createRouter({
  routeTree,
  context: { auth: {} },
})
```

Child routes inherit context. `beforeLoad` may return additional context for
the current route and its descendants. This supports authentication,
authorization, data clients, themes, and request-scoped utilities.

## TanStack Query integration

When Query owns freshness, set Router's preload staleness to zero and expose a
request-appropriate `QueryClient` through router context.

```tsx
const router = createRouter({
  routeTree,
  context: { queryClient },
  defaultPreloadStaleTime: 0,
})
```

Use `ensureQueryData` or `prefetchQuery` in loaders and consume the same query
with `useSuspenseQuery` in components. For SSR, create a fresh QueryClient for
each request. A module-level server singleton can leak cached user data.

## Rendering and lifecycle areas

- Pending, error, and not-found boundaries
- Deferred data and `<Await>`
- Manual and automatic code splitting
- Document head management
- SSR and hydration
- Render optimization with selected route state
- Router events and invalidation

## Mutations

Router does not prescribe a mutation client. After a successful mutation,
invalidate the external cache and/or call `router.invalidate()` when route
loaders must re-run. Keep mutation side effects out of render functions.

## Failure modes

- Assuming a client-first Router loader is server-only exposes server secrets.
- Duplicating freshness policy in Router and Query produces stale or redundant
  work.
- Reading all router state when only one field is needed causes avoidable
  rerenders.
- Throwing an ordinary error for an expected not-found case bypasses the
  Router's dedicated not-found handling.

## Gaps

The Router docs cover SSR at the Router level, but full-stack server execution,
server functions, middleware, deployment output, and selective SSR belong to
TanStack Start and must not be inferred from this package.

## Sources

- https://tanstack.com/router/latest/docs/guide/preloading.md
- https://tanstack.com/router/latest/docs/guide/router-context.md
- https://tanstack.com/router/latest/docs/guide/external-data-loading.md
- https://tanstack.com/router/latest/docs/integrations/query.md
- https://tanstack.com/router/latest/docs/guide/ssr.md
- https://tanstack.com/router/latest/docs/guide/not-found-errors.md
