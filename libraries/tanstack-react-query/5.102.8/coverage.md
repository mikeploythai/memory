---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "coverage map"
source: "https://tanstack.com/query/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-query@5.102.8; commit 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Coverage map

## Sources

| Source | Result |
|---|---|
| `https://tanstack.com/query/latest/llms.txt` | Machine-readable corpus index |
| `https://tanstack.com/query/latest/docs/index.md` | Markdown documentation index |
| Product `llms-full.txt` | Not present; returned 404 on 2026-08-31 |
| `https://github.com/TanStack/query` | Official repository |
| Tag `@tanstack/react-query@5.102.8` | Resolved to commit `2969edf32f7e0c48e2a108d84712d6e01edfde21` |
| Pinned `docs` tree | 497 Markdown files; recursive tree was not truncated |

## Package and framework alignment

| Package | Stable version |
|---|---:|
| `@tanstack/react-query`, `query-core`, React Devtools, ESLint | 5.102.8 |
| Solid, Vue, and Preact Query | 5.102.8 |
| Angular Query | 5.102.8, package explicitly experimental |
| Svelte Query | 6.1.48 |
| Lit Query | 0.2.20 |

The hosted corpus is broadly labeled `v5 Latest`. That label is not a valid
version slug for Svelte or Lit and does not replace exact npm evidence.

## Bootstrap chain

| Requirement | Evidence | Status |
|---|---|---|
| Package choice and prerequisites | React package, React 18+, browser floor in [bootstrap](bootstrap-query-client-and-defaults.md) | ready |
| Project creation | Query assumes an existing host application | not applicable |
| Installation | Runtime and recommended ESLint commands in [bootstrap](bootstrap-query-client-and-defaults.md) | partial; commands are unpinned and therefore do not reproduce exact `5.102.8` without an added version |
| Core configuration | QueryClient and provider in [bootstrap](bootstrap-query-client-and-defaults.md) | ready |
| Mental model | Keys, functions, observers, stale data, and cache lifecycle indexed | ready |
| Minimal runnable application | Query component is complete, but host renderer/project is external | partial |
| Verification/build | Observable component states documented; no official host run/build command | partial |

Greenfield setup remains partial because Query is a library integrated into a
separately bootstrapped React application.

## Task readiness

| Task | Status | Indexed evidence |
|---|---|---|
| Greenfield setup | partial | [bootstrap](bootstrap-query-client-and-defaults.md) |
| Common query and cache work | ready | [query lifecycle](queries-cache-and-data-lifecycle.md) |
| Mutations and invalidation | ready | [mutations](mutations-invalidation-and-optimistic-updates.md) |
| Debugging | partial | Defaults and failure modes indexed; Devtools detail deferred |
| Migration | partial | Migration inventory present; detailed source/target transformations deferred |
| Production/build concerns | partial | SSR, persistence, and testing mapped; host deployment is external |

## Substantive source-section mapping

| Source section | Inventory | Memory status |
|---|---:|---|
| Getting Started | 43 pages across seven adapters | React bootstrap indexed; other adapters deferred |
| Guides & Concepts | 174 pages | React core lifecycle and mutation areas indexed; adapter variants deferred |
| ESLint | 9 pages | package noted; individual rules deferred |
| Plugins | 14 pages | React persistence families mapped; detailed/other adapter pages deferred |
| API Reference | 256 generated entries | API families mapped; signatures deferred |
| Examples | 58 pages | overview example adapted; gallery deferred |
| Core repository reference | 12 pages | classes/managers mapped in operations page |

## Recipes, warnings, and troubleshooting

| Category | Status |
|---|---|
| Queries, keys, cancellation, dependent work | indexed |
| Pagination, infinite queries, and prefetch | partial; lifecycle guidance is indexed, but complete pagination and `useInfiniteQuery` implementations are deferred |
| Mutations, invalidation, rollback | indexed |
| SSR and hydration | partial; framework transfer details deferred |
| Persistence | partial; package/API details deferred |
| Testing | partial; provider isolation pattern indexed |
| Devtools troubleshooting | deferred |
| ESLint anti-pattern detection | deferred |
| React Native, GraphQL, Suspense | deferred |

## Migrations and API areas

React migration guides to v3, v4, and v5 are inventoried. Vue v5 and Svelte v6
migrations are recorded as other-library work. API coverage includes QueryClient,
caches, observers, managers, hydration, hooks, helpers, and result types, but not
individual signatures.

## Meaningful gaps

- No product-specific `llms-full.txt`.
- The quick start assumes `getTodos`, `postTodo`, a renderer, and an existing
  application; it is illustrative rather than a complete project bootstrap.
- Framework documentation generations do not align to one package version.
- Experimental APIs and the Angular package need visible stability markers.
- Exact host build, deployment, and SSR serialization behavior is framework
  owned and cannot be inferred from Query alone.

## Bounded stopping point

This five-file batch covers the React adapter's bootstrap, defaults, query/cache
lifecycle, mutations, SSR/persistence/testing map, migrations, and API families.
It defers generated API signatures, individual ESLint rules, Devtools options,
most examples, and every non-React adapter's implementation details.

