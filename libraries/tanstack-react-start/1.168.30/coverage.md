---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "documentation coverage map"
source: "https://github.com/TanStack/router/tree/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Documentation coverage map

This map records the bounded first depth batch for React Start 1.168.30. `indexed` means a retrieval page exists in this directory. `deferred` means the immutable tag contains authoritative material reserved for another batch. `not present` means the exact-tag documentation has no dedicated page.

## Bootstrap chain

| Required step | Status | Memory evidence |
|---|---|---|
| Package choice, framework scope, and prerequisites | ready | `overview-and-package-choice.md` |
| Project creation and installation | ready | `getting-started.md` |
| Exact-version manual setup | ready | `build-from-scratch.md` |
| Required plugins, files, document shell, and generated route tree | ready | `build-from-scratch.md`, `routing.md` |
| Minimal runnable application | ready | `build-from-scratch.md`, `routing.md` |
| Development and production-build verification | ready | `build-from-scratch.md`, `routing.md` |
| Setup mistakes and version-sensitive caveats | ready | `getting-started.md`, `build-from-scratch.md`, `routing.md` |

## Task readiness

| Task | Status | Evidence or gap |
|---|---|---|
| Greenfield Start project | ready | Complete bootstrap chain above; feature pages cover server boundaries, middleware, auth, rendering, and hosting |
| Common full-stack feature work | partial | Server functions, routes, auth, middleware, and streaming are indexed; databases, styling, and integration examples remain deferred |
| Debugging | partial | Hydration, environment, import-boundary, middleware, and observability failures are indexed; the dedicated error-boundaries page remains deferred |
| Migration | partial | Greenfield target behavior is indexed; framework-specific migration pages remain deferred |
| Local production build and run | ready | Pinned scripts, Nitro output, client/server entry points, build-time type and import-protection checks, and a local production smoke test are indexed |
| Provider deployment and hosting | partial | Hosting concepts and observability are indexed, but provider adapters, provider configuration, and deployment commands remain external/deferred |

## Indexed in this batch

| Status | Memory page | Exact-tag source topics |
|---|---|---|
| indexed | `overview-and-package-choice.md` | overview, Start versus Router, prerequisites |
| indexed | `getting-started.md` | Builder, CLI, examples, manual-setup routing |
| indexed | `build-from-scratch.md` | installation, TypeScript, build plugins, required files, first route, run/build verification |
| indexed | `routing.md` | router factory, root document, file routes, generated route tree |
| indexed | `execution-model-and-code-boundaries.md` | execution model, execution patterns |
| indexed | `server-functions.md` | server functions |
| indexed | `environment-functions-and-import-protection.md` | environment functions, import protection |
| indexed | `environment-variables-and-secrets.md` | environment variables, import protection |
| indexed | `middleware.md` | middleware |
| indexed | `server-routes-vs-server-functions.md` | server routes and server functions |
| indexed | `streaming-and-server-components.md` | streamed server-function data, server components |
| indexed | `hydration-errors-and-deferred-hydration.md` | hydration errors, deferred hydration |
| indexed | `selective-ssr-spa-and-prerendering.md` | selective SSR, SPA mode, static prerendering |
| indexed | `authentication-and-server-primitives.md` | authentication overview, primitives, guide |
| indexed | `server-client-entry-points.md` | server and client entries |
| indexed | `hosting-and-observability.md` | hosting and observability |

## Deferred exact-tag corpus

- Orientation and migration: `comparison.md`, `start-vs-nextjs.md`, `migrate-from-next-js.md`.
- Tutorials: `tutorial/reading-writing-file.md`, `tutorial/fetching-external-api.md`.
- Server/execution: `path-aliases.md`, `static-server-functions.md`, `error-boundaries.md`. Their related concepts are mentioned here but the dedicated pages remain deferred.
- Rendering: `guide/isr.md`, `early-hints.md`, `cdn-asset-urls.md`. Incremental regeneration is not implied by the static-prerendering page.
- Data: `guide/databases.md`.
- Styling and metadata: `guide/css-styling.md`, `tailwind-integration.md`, `rendering-markdown.md`, `seo.md`, `geo.md`.
- Exact-tag examples exposed by the docs corpus: basic, Basic with React Query, Clerk, DIY auth, Supabase, Convex/Trellaux, WorkOS, Material UI, Auth.js, static rendering, and Cloudflare. These are deferred as integration-specific recipe pages.
- Router concepts used by Start remain versioned under the Router package. Start's routing guide should be indexed later with explicit cross-version provenance rather than copying current Router `latest` behavior.
- Package source and type declarations under `packages/react-start` are deferred for a separate API-signature batch.

## Not present as dedicated exact-tag pages

- No standalone Start API reference section comparable to Router or Query. Exact signatures not covered by guides must be verified in package source/types at this release tag.
- No single anti-pattern or security reference. This batch keeps each failure mode attached to its execution, import, auth, middleware, or hydration source.
- No guarantee that hosted `latest` matches 1.168.30. Start was in a release-candidate/pre-stable period, so the immutable package tag is required.

Stopping point: a complete four-page bootstrap chain, twelve depth pages, and this map. The remaining guides, examples, Router cross-links, and package API source are explicitly deferred.

## Sources

- https://tanstack.com/start/latest/llms.txt
- https://github.com/TanStack/router/tree/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react
- https://github.com/TanStack/router/tree/62a191baa068e9a2d27815cc82fb2a16690fedea/packages/react-start

