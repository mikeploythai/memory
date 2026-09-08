---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "coverage map"
source: "https://tanstack.com/router/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Coverage map

## Sources

| Source | Result |
|---|---|
| `https://tanstack.com/router/latest/llms.txt` | Machine-readable index; 102 documentation and example links plus four roots |
| `https://tanstack.com/router/latest/docs/index.md` | Markdown equivalent of the documentation index |
| Product `llms-full.txt` | Not present; returned 404 on 2026-08-31 |
| `https://github.com/TanStack/router` | Official monorepo |
| Release tag `@tanstack/react-router@1.170.32` | Resolved to commit `a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2` |
| Pinned `docs/router` tree | 162 Markdown files; GitHub recursive tree was not truncated |

## Package alignment

| Package | Stable version checked |
|---|---:|
| `@tanstack/react-router` | 1.170.32 |
| `@tanstack/router-core` | 1.171.27 |
| `@tanstack/router-generator` | 1.167.33 |
| `@tanstack/router-plugin` | 1.168.35 |
| `@tanstack/router-cli` | 1.167.33 |
| `@tanstack/react-router-devtools` | 1.167.1 |

These packages are independently versioned. Example dependency sets must record
every package version instead of assigning the Router adapter version to all of
them.

## Bootstrap chain

| Requirement | Evidence | Status |
|---|---|---|
| Package choice and prerequisites | React 18+, ReactDOM 18+, TypeScript 5.3+ recommended in [bootstrap](bootstrap-and-tooling.md) | ready |
| Project creation | `npx @tanstack/cli create --router-only` in [bootstrap](bootstrap-and-tooling.md) | partial; the CLI target is mutable and unversioned |
| Installation | Runtime, devtools, and plugin commands in [bootstrap](bootstrap-and-tooling.md) | partial; package commands are unpinned |
| Manual setup | Vite configuration, provider, and generated-tree wiring in [bootstrap](bootstrap-and-tooling.md) | partial; complete root, index, and example route files are not retained |
| Core mental model | Typed route tree, URL state, loaders, and context in the routing and data pages | ready |
| Minimal runnable application | Complete Router provider plus documented route-file shape in [bootstrap](bootstrap-and-tooling.md) | partial |
| Verification/build | Generated-tree and browser checks are known, but host scripts are bundler-specific and not fully supplied | partial |

Greenfield setup is not marked ready because the indexed source does not provide
one complete, universal host `package.json`, HTML, routes, scripts, and build
result in a single pinned example.

## Task readiness

| Task | Status | Indexed evidence |
|---|---|---|
| Greenfield setup | partial | [bootstrap](bootstrap-and-tooling.md) |
| Common routing and URL-state work | ready | [routing and URL state](routing-navigation-and-url-state.md) |
| Data loading and cache integration | partial | [data loading](data-loading-rendering-and-context.md) covers loaders and cache boundaries; complete Query provider, context, and hydration wiring are deferred |
| Debugging | partial | Failure modes are indexed; source-only debugging how-to remains deferred |
| Migration | partial | [migration map](migrations-and-api-map.md); no end-to-end verified migrated app |
| Production/build concerns | partial | SSR concepts indexed; deployment and bundler-specific verification deferred |

## Substantive source-section mapping

| Source section | Inventory | Memory status |
|---|---:|---|
| Getting Started | 6 pages | Bootstrap and mental model indexed; comparison/FAQ deferred |
| Installation Guides | 8 pages | Manual and Vite covered; Rsbuild, Webpack, Esbuild, CLI details deferred |
| Core Routing | 8 pages | Indexed in routing page |
| Navigation & URL State | 11 pages | Indexed at section level; specialist recipes deferred |
| Data & Rendering | 10 pages | Indexed at section level |
| Router Configuration | 9 pages | Context and core creation covered; events/static data deferred |
| Integrations | 1 page | Query integration partially indexed; complete provider, context, and hydration wiring are deferred |
| ESLint | 2 pages | deferred |
| API | 2 indexed aggregators; 81 pinned source files | Symbol map indexed; per-symbol content deferred |
| Examples | 46 pages | Quick-start shapes used; remaining examples deferred |
| Release-tree how-to | 25 files including README/drafts | omitted by `llms.txt`; active recipes deferred, drafts excluded |

## Recipes, warnings, and troubleshooting

| Category | Status |
|---|---|
| File- and code-based setup | indexed |
| Search validation and typed navigation | indexed |
| Query integration | partial |
| Authentication and authorization | partial through context; dedicated how-to deferred |
| Testing | not indexed; official how-to exists in pinned tree |
| Debugging | not indexed; official `debug-router-issues.md` exists |
| Deployment | not indexed; official `deploy-to-production.md` exists |
| Anti-patterns | Generated-file editing, unvalidated search, singleton SSR QueryClient, and duplicate cache policy recorded |

## Migrations and API areas

React Router and React Location migration guides are mapped in
[migrations-and-api-map.md](migrations-and-api-map.md). The API map covers
creation functions, components, hooks, classes, and major option types. Detailed
per-symbol signatures remain deferred.

## Meaningful gaps

- No product-specific `llms-full.txt` corpus.
- `llms.txt` omits the how-to tree and most per-symbol Router API files.
- Hosted docs are labeled `v1 Latest`, not exact package patch versions.
- The manual setup lacks one complete bundler-independent build verification.
- Solid and Vue adapters have different stable versions and are outside this
  React package directory.

## Bounded stopping point

This five-file batch covers React Router bootstrap, routing and URL state, data
loading and context, migrations, and an API map. It intentionally defers
bundler-specific installations, ESLint rules, the active how-to corpus,
per-symbol API pages, Solid/Vue adapters, and the full example gallery.

