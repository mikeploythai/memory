---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "routing, navigation, and URL state"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/routing/routing-concepts.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Routing, navigation, and URL state

TanStack Router builds a typed route tree. A match carries pathname, path
parameters, validated search state, loader data, route context, and status.
File-based and code-based routes can coexist.

## Route-tree choices

- File-based routing generates a route tree from files under `src/routes`.
- Code-based routing composes `createRootRoute`, `createRoute`, and
  `addChildren` directly.
- Virtual file routes describe a generated tree without requiring every route
  to correspond to a physical route file.
- Pathless layouts group and wrap child routes without adding a URL segment.

```tsx
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/posts/$postId')({
  component: Post,
})

function Post() {
  const { postId } = Route.useParams()
  return <p>Post {postId}</p>
}
```

## Typed links and navigation

Use `Link` for rendered navigation and `useNavigate` for imperative navigation.
The registered router supplies destination, parameter, and search types.

```tsx
import { Link } from '@tanstack/react-router'

<Link
  to="/posts/$postId"
  params={{ postId: '42' }}
  search={{ preview: true }}
>
  Preview post
</Link>
```

Relative navigation is resolved from a route's location. `linkOptions` can
define reusable typed options without rendering a link. Custom links should
preserve the Router link props and ref behavior.

## Search parameters

Search parameters are application state in the URL. Validate them at a route
boundary instead of reading untyped strings throughout the component tree.

```tsx
type ProductSearch = {
  page: number
  filter: string
}

export const Route = createFileRoute('/products')({
  validateSearch: (search): ProductSearch => ({
    page: Number(search.page ?? 1),
    filter: String(search.filter ?? ''),
  }),
  component: Products,
})

function Products() {
  const { page, filter } = Route.useSearch()
  return <p>{filter || 'All products'}: page {page}</p>
}
```

Use search middleware for retained, stripped, or transformed search values.
Custom serializers are appropriate when the default JSON-first encoding does
not match an application's URL contract.

## URL behavior covered by the official guides

- Path parameters and route matching
- Search validation, navigation, and custom serialization
- Route masking and URL rewrites
- Navigation blocking
- Browser, hash, and memory history
- Scroll restoration
- Internationalized routing

## Failure modes

- Omitting router registration weakens cross-route type inference.
- Treating raw search values as trusted bypasses route-level validation.
- Editing `routeTree.gen.ts` loses changes on the next generation pass.
- A pathless layout and a path-bearing layout produce different URLs even if
  their component nesting looks identical.
- Route masks change the displayed location; code that needs the resolved
  location must not assume the visible URL is the matched route.

## Gaps

The navigation corpus is extensive, but the top-level `llms.txt` index does not
surface the release tree's additional search-parameter how-to pages. Those
recipes should be inventoried separately before declaring all URL-state recipes
indexed.

## Sources

- https://tanstack.com/router/latest/docs/routing/route-trees.md
- https://tanstack.com/router/latest/docs/routing/file-based-routing.md
- https://tanstack.com/router/latest/docs/routing/code-based-routing.md
- https://tanstack.com/router/latest/docs/guide/navigation.md
- https://tanstack.com/router/latest/docs/guide/path-params.md
- https://tanstack.com/router/latest/docs/guide/search-params.md
- https://tanstack.com/router/latest/docs/guide/navigation-blocking.md
