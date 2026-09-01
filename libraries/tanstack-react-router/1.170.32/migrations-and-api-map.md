---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "migrations and API map"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/api/router.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Migrations and API map

The hosted index presents two API aggregators, while the pinned source tree has
81 Router API Markdown files. Use the aggregate page to discover symbols and
the pinned per-symbol file when exact signatures or options matter.

## Creation APIs

- `createRouter`
- `createRootRoute` and `createRootRouteWithContext`
- `createRoute`
- `createFileRoute` and `createLazyFileRoute`
- `createLazyRoute`
- `createRouteMask`
- `getRouteApi`

## Navigation and rendering APIs

- `Link`, `Navigate`, `Outlet`, and `MatchRoute`
- `Await` and `ClientOnly`
- `CatchBoundary`, `CatchNotFound`, and `ErrorComponent`
- `redirect`, `notFound`, `isRedirect`, and `isNotFound`
- `linkOptions`, `retainSearchParams`, and `stripSearchParams`

## Hooks

- `useNavigate`, `useLocation`, and `useRouter`
- `useMatch`, `useMatches`, and `useMatchRoute`
- `useParams` and `useSearch`
- `useLoaderData` and `useLoaderDeps`
- `useRouteContext` and `useRouterState`
- `useBlocker` and `useCanGoBack`
- `useLinkProps`, `useAwaited`, and match-family hooks

## Important types and classes

- `Router`, `Route`, `RouteApi`, and `FileRoute`
- `RouterOptions`, `RouterState`, and `RouterEvents`
- `RouteOptions`, `RouteMatch`, and `RouteMask`
- `LinkOptions`, `LinkProps`, `NavigateOptions`, and `ToOptions`
- `ParsedLocation`, `ParsedHistoryState`, `Redirect`, and `NotFoundError`
- The `Register` interface used for module augmentation

## Migration from React Router

The official guide maps concepts rather than promising mechanical conversion.
Key changes include:

1. Replace route-element configuration with a typed route tree.
2. Choose file-based generation or explicit code-based composition.
3. Replace React Router links and navigation hooks with typed Router APIs.
4. Move path and search validation to route definitions.
5. Move data loading into route loaders or an integrated external cache.
6. Register the router type so navigation is inferred across the application.

Do not confuse `@tanstack/react-router` with the unrelated `react-router` and
`react-router-dom` packages.

## Migration from React Location

The dedicated guide covers the predecessor library. Preserve URL behavior and
data-loading semantics first, then adopt generated routes and stronger inferred
types. Test search serialization because URL-state contracts commonly outlive
the routing implementation.

## API evidence gaps

- Product `llms.txt` lists only `router.md` and `file-based-routing.md`.
- The release tree contains 79 additional per-symbol API pages.
- The public navigation does not expose all release-tree how-to pages.
- Generated API text may document exported types without explaining lifecycle
  interactions; pair it with the relevant guide.
- There is no single official end-to-end migration covering loaders, SSR,
  external Query integration, tests, and deployment together.

## Source selection rule

For 1.170.32 implementation questions, prefer the per-symbol file at commit
`a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2` over a moving `main` page. If a
companion package API is involved, pin that package separately rather than
assuming it also has version 1.170.32.

## Sources

- https://tanstack.com/router/latest/docs/api/router.md
- https://tanstack.com/router/latest/docs/api/file-based-routing.md
- https://tanstack.com/router/latest/docs/installation/migrate-from-react-router.md
- https://tanstack.com/router/latest/docs/installation/migrate-from-react-location.md
- https://github.com/TanStack/router/tree/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/api
- https://github.com/TanStack/router/tree/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to
