---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "file-based routing and naming conventions"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/routing/file-based-routing.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# File-based routing and naming conventions

File-based routing turns files under the configured routes directory into a generated route tree. Each route file exports `Route`, normally created with `createFileRoute`. The bundler plugin or Router CLI watches the directory, writes the route path argument, and regenerates `routeTree.gen.ts`. That generated file should be excluded from formatting and lint rules and should not be edited by hand.

Route filenames encode hierarchy. Dots and directories can both express nesting. `index` identifies an index route, `$name` creates a required path parameter, and a trailing splat captures the rest of the path. An underscore prefix creates a pathless layout; a trailing underscore breaks a route out of a parent nesting relationship. Parentheses form organizational route groups without changing the URL. Square brackets escape characters that would otherwise be interpreted by the naming grammar.

Files and directories prefixed with the configured ignore prefix are excluded, which allows components and utilities to remain near their routes. Virtual file routes can combine a programmatic route definition with file-backed route modules when the filesystem alone cannot express the desired organization.

Configuration has sharp edges. Do not configure `routeFilePrefix`, `routeFileIgnorePrefix`, `routeFileIgnorePattern`, `indexToken`, or `routeToken` so that their meanings overlap. The exact-version API warns that token collisions can produce unexpected routing behavior. Keep `routesDirectory` and `generatedRouteTree` relative to the working directory, and regenerate after moves or renames before relying on inferred types.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/routing/file-based-routing.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/routing/file-naming-conventions.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/api/file-based-routing.md


