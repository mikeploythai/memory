---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "documentation coverage map"
source: "https://github.com/TanStack/router/tree/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Documentation coverage map

This map records the bounded first depth batch for React Router 1.170.32. `indexed` means this draft directory contains a retrieval page. `deferred` means the source exists at the immutable tag but was deliberately left for a later batch. `not present` means the exact-tag docs have no dedicated page; claims must be extracted from named primary pages or verified against package source.

## Indexed in this batch

| Status | Memory page | Exact-tag sources |
|---|---|---|
| indexed | `routing-and-route-trees.md` | `routing/routing-concepts.md`, `routing/route-trees.md` |
| indexed | `file-based-routing.md` | `routing/file-based-routing.md`, `routing/file-naming-conventions.md`, `api/file-based-routing.md` |
| indexed | `search-params-validation-and-serialization.md` | `guide/search-params.md`, `guide/custom-search-param-serialization.md` |
| indexed | `navigation-links-and-blocking.md` | `guide/navigation.md`, `guide/link-options.md`, `guide/navigation-blocking.md` |
| indexed | `data-loading-cache-and-revalidation.md` | `guide/data-loading.md`, `guide/data-mutations.md` |
| indexed | `preloading-and-code-splitting.md` | `guide/preloading.md`, `guide/code-splitting.md`, `guide/automatic-code-splitting.md` |
| indexed | `external-data-loading-and-query.md` | `guide/external-data-loading.md`, `integrations/query.md` |
| indexed | `authentication-and-route-context.md` | `guide/authenticated-routes.md`, `guide/router-context.md` |
| indexed | `errors-not-found-and-redirects.md` | `guide/not-found-errors.md`, redirect/not-found API pages |
| indexed | `ssr-and-deferred-data.md` | `guide/ssr.md`, `guide/deferred-data-loading.md` |
| indexed | `testing-and-debugging.md` | three `how-to` testing/debugging pages |
| indexed | `migrate-from-react-router.md` | migration how-to and installation guide |

## Deferred exact-tag corpus

- Getting started: `overview.md`, `quick-start.md`, `devtools.md`, `decisions-on-dx.md`, `comparison.md`, `faq.md`.
- Installation: `installation/manual.md`, `with-vite.md`, `with-rspack.md`, `with-webpack.md`, `with-esbuild.md`, `with-router-cli.md`, `migrate-from-react-location.md`.
- Routing: `routing/route-matching.md`, `virtual-file-routes.md`, `code-based-routing.md`.
- Navigation and URL state: `guide/custom-link.md`, `path-params.md`, `route-masking.md`, `history-types.md`, `scroll-restoration.md`, `internationalization-i18n.md`, `url-rewrites.md`.
- Rendering and configuration: `guide/document-head-management.md`, `render-optimizations.md`, `creating-a-router.md`, `outlets.md`, `router-events.md`, `type-safety.md`, `type-utilities.md`, `static-route-data.md`, `parallel-routes.md`.
- How-to recipes: install, deploy, environment variables, arrays/objects/dates in search, basic/shared/navigation search params, auth providers, RBAC, SSR, and Chakra/Framer Motion/Material UI/shadcn integrations. Files under `how-to/drafts/` are excluded until published.
- ESLint: `eslint/eslint-plugin-router.md`, `eslint/create-route-property-order.md`.
- API: `api/router.md` and every symbol page under `api/router/` are deferred as a dedicated API batch. The directory covers route constructors, Router and Route classes/options, Link/navigation types, hooks, history/location types, boundaries, redirects, and not-found helpers.
- Runnable React examples under `examples/react/` are deferred as a recipe-validation batch; generated `routeTree.gen.ts` files are evidence, not content to copy.

## Not present as dedicated exact-tag pages

- No single official “anti-patterns” page. Pitfalls in this batch are extracted only from the indexed guides and API warnings.
- No single security reference. Client route guards must not be presented as server authorization.
- No guarantee that hosted `latest` Markdown matches 1.170.32; it is discovery-only after this stopping point.

Stopping point: twelve high-value semantic pages plus this map. No remaining guide, symbol API page, example, draft, or package source was silently indexed.

## Sources

- https://tanstack.com/router/latest/llms.txt
- https://github.com/TanStack/router/tree/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router
- https://github.com/TanStack/router/tree/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/examples/react

