---
library: "@tanstack/react-start"
version: "1.168.49"
topic: "coverage map"
source: "https://tanstack.com/start/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.49; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Coverage map

## Sources

| Source | Result |
|---|---|
| `https://tanstack.com/start/latest/llms.txt` | Machine-readable documentation and example index |
| `https://tanstack.com/start/latest/docs/index.md` | Markdown documentation index |
| Product `llms-full.txt` | Not present; returned 404 on 2026-08-31 |
| `https://github.com/TanStack/router` | Official Router and Start monorepo |
| Tag `@tanstack/react-start@1.168.49` | Resolved to commit `a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2` |
| Pinned `docs/start` tree | 82 Markdown files; recursive tree was not truncated |

## Product and package alignment

The docs navigation says `v0 Latest`, and the overview labels Start Release
Candidate. npm publishes `@tanstack/react-start` 1.168.49 under `latest`.

| Package | Stable version |
|---|---:|
| `@tanstack/react-start` | 1.168.49 |
| `@tanstack/react-start-client` | 1.168.30 |
| `@tanstack/react-start-server` | 1.167.37 |
| `@tanstack/start-client-core` | 1.170.27 |
| `@tanstack/start-server-core` | 1.169.31 |
| `@tanstack/start-plugin-core` | 1.171.39 |
| `@tanstack/react-router` | 1.170.32 |

## Bootstrap chain

| Requirement | Evidence | Status |
|---|---|---|
| Package choice and prerequisites | Start versus Router choice and Vite/Rsbuild dependencies documented; exact runtime/tooling ranges are not retained | partial |
| Project creation | CLI and example-clone commands in [bootstrap](bootstrap-and-build-from-scratch.md) both follow mutable targets | partial |
| Installation | npm commands are retained, but package versions are unpinned | partial |
| Manual setup | Scripts, Vite config, required filenames, and router factory are indexed; the complete TypeScript config and route-file contents are missing | partial |
| Core mental model | Router-first app plus explicit server boundaries indexed | ready |
| Minimal runnable application | Official counter behavior and full-document requirements are summarized, but complete `__root.tsx` and `index.tsx` contents are not retained | partial |
| Verification/build | Commands and expected localhost behavior are indexed, but the incomplete setup cannot be reproduced from this batch alone | partial |

The React/Vite greenfield chain is partial. This batch does not retain every
required file, the complete TypeScript configuration, or an exact companion-
package set. The basic-example clone also follows the mutable `main` branch.
Production startup and deployment remain provider-specific.

## Task readiness

| Task | Status | Indexed evidence |
|---|---|---|
| Greenfield React/Vite setup | partial | [bootstrap](bootstrap-and-build-from-scratch.md) lacks complete route files, full TypeScript configuration, and pinned package versions |
| Common server work | partial | [execution and server functions](execution-server-functions-and-middleware.md) preserves the model and selected snippets; complete invocation, middleware attachment, and server-route implementations are deferred |
| Rendering and SSR selection | partial | [rendering and hosting](rendering-ssr-and-hosting.md) preserves the mode model; executable route-level selection and root-shell handling are deferred |
| Debugging | partial | Hydration and boundary failure modes indexed; observability details deferred |
| Migration | partial | Next.js mapping indexed; no verified migrated application |
| Production/build concerns | partial | Build and provider patterns indexed; universal production start is not present |

## Substantive source-section mapping

| Source section | Inventory | Memory status |
|---|---:|---|
| Getting Started | 9 React/Solid pages | React overview, setup, scratch build, and migration indexed |
| Tutorials | 4 pages | deferred |
| Server & Execution | 26 React/Solid pages | partial; React execution and boundaries are mapped, while complete functions, middleware attachment, and server-route implementations are deferred |
| Rendering | 18 React/Solid pages | partial; React SSR, hydration, static modes, and entries are mapped without complete route-level implementations |
| Deployment & Operations | 4 pages | React hosting indexed; observability deferred |
| Authentication & Data | 8 pages | React boundary model indexed; provider details deferred |
| Styling & Metadata | 9 pages | deferred |
| Examples | 22 pages | Basic example used for bootstrap; remaining examples deferred |
| API reference | not present | Public families mapped from guides/source; exact signatures deferred |

## Recipes, warnings, and troubleshooting

| Category | Status |
|---|---|
| Vite setup and generated routes | indexed |
| Execution boundaries and import protection | indexed |
| Server functions, middleware, server routes | partial |
| Selective SSR, SPA, hydration | partial |
| Static rendering and ISR | partial |
| Cloudflare and Netlify hosting | partial; provider pinning still required |
| Authentication and databases | partial; provider implementation deferred |
| Observability | deferred |
| CSS, Tailwind, Markdown, SEO, GEO | deferred |
| Error boundaries and hydration troubleshooting | partial |

## Migrations and API areas

Next.js migration is indexed at the architectural level. Remix 2 / React Router
7 migration is explicitly not present. Start has no consolidated API reference;
the mapped families include server functions, middleware, environment helpers,
Start configuration, entry components, and Router re-exports.

## Meaningful gaps

- Product-specific `llms-full.txt` is absent.
- Hosted `v0 Latest`, RC status, and npm 1.x stable versions disagree in label.
- Companion packages are independently versioned.
- The retained manual install does not pin companion-package versions, and the
  scaffold and example commands follow mutable targets.
- Complete `tsconfig.json`, `src/routes/__root.tsx`, and
  `src/routes/index.tsx` contents are not retained, so greenfield setup cannot
  be completed from this batch alone.
- No consolidated API/reference section exists.
- No universal production-start command or deployment artifact applies to every
  hosting adapter.
- React Server Components are described as experimental and are not indexed in
  this batch.

## Bounded stopping point

This five-file batch covers React/Vite bootstrap, execution boundaries, server
functions and middleware, rendering/SSR/hosting, authentication boundaries,
Next.js migration, and API gaps. It defers Solid/Vue Start, tutorials,
observability, styling/metadata, provider-specific auth and databases,
experimental server components, detailed static generation, and most examples.

