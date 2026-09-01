---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "routing concepts and route trees"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/routing/routing-concepts.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Routing concepts and route trees

TanStack Router models an application as a typed route tree. The root route has no path, always matches, and wraps every other match. Child routes inherit their parent path, context, search schema, and rendering position. Pathless layout routes participate in nesting without adding a URL segment; non-nested routes can break out of a parent's path hierarchy while remaining colocated in the source tree.

The tree can be produced from files or assembled in code. File-based routing uses `createFileRoute` and a generated route tree. Code-based routing uses `createRootRoute`, `createRoute`, and explicit `addChildren` calls. Both approaches produce the same runtime model, but file-based routing gives the generator enough information to keep route paths and TypeScript registration synchronized.

A matched branch renders from the root through its descendants. Each route can contribute a component, loader, search validation, context, pending UI, error UI, and not-found UI. An `Outlet` renders the next child match. Index routes match their parent path exactly, dynamic segments capture values, splat segments capture a remainder, and pathless layouts group behavior without changing the URL.

Treat the generated tree as an application contract. Links, loaders, route hooks, params, and search values derive their types from it. If a route is moved or renamed, regenerate the tree before diagnosing downstream type errors. Do not hand-edit generated route-tree output; change the route definitions or generator configuration instead.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/routing/routing-concepts.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/routing/route-trees.md


