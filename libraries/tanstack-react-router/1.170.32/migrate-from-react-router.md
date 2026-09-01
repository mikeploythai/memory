---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "migration from React Router"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to/migrate-from-react-router.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Migration from React Router

Treat migration as a route-contract rewrite, not an import rename. TanStack Router derives navigation, params, search, loaders, and route hooks from its registered tree. Start by choosing file-based or code-based routing, create the root route and router, then migrate one route branch at a time while preserving URLs.

Replace React Router route configuration with TanStack route definitions. File-based projects export `Route` from route files and generate the tree; code-based projects assemble children explicitly. Replace `Outlet`, link, navigation, params, location, and match APIs with their TanStack equivalents, but also add the route identity needed for strict typing. Relative navigation should supply `from` rather than assuming component nesting.

Move URL search parsing into `validateSearch`. React Router applications often read strings directly from `URLSearchParams`; TanStack Router expects validation to normalize external values before loaders and components use them. Move route data fetching into loaders when navigation-time preloading is desired, or integrate an external cache through router context.

Redirects, not-found results, pending UI, and errors are route control flow and boundaries, not component-only effects. Migrate auth guards into `beforeLoad` and keep server authorization in the data layer. Do not import patterns from Next.js or Remix such as `getServerSideProps`, App Router file names, or standalone Remix loader exports; they are different contracts.

Run both routers only behind an explicit boundary during an incremental migration. Two routers should not compete for the same history or intercept the same links. After each branch moves, verify direct loading, Back/Forward, params, search round-tripping, redirects, and error boundaries before removing the old route.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to/migrate-from-react-router.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/installation/migrate-from-react-router.md


