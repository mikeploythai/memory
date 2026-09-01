---
library: "@tanstack/table-core"
version: "9.2.4"
topic: "coverage map"
source: "https://tanstack.com/table/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/table-core@9.2.4 (d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6)"
---

# TanStack Table 9.2.4 coverage map

## First-party sources inspected

- https://tanstack.com/table/latest/llms.txt
- https://tanstack.com/table/latest/docs/index.md
- https://github.com/TanStack/table/tree/%40tanstack%2Ftable-core%409.2.4/docs
- https://github.com/TanStack/table/releases/tag/%40tanstack%2Ftable-core%409.2.4
- npm `latest` metadata for every package in `packages/*/package.json`

The hosted docs and release tree had the same documentation paths when checked.
The hosted `/latest` routes remain moving sources; the tag above is immutable.

## Bootstrap chain

| Requirement | Evidence | Status | Notes |
|---|---|---|---|
| Package choice and prerequisites | [installation](installation-and-package-choice.md) | partial | Package matrix is complete; framework project and runtime prerequisites are delegated. |
| Project creation and installation | [installation](installation-and-package-choice.md) | partial | Exact package commands are recorded; no official project generator is prescribed. |
| Getting started / quick start | [React quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md) | ready | The pinned v9 React component uses `tableFeatures`, the automatic core row model, and `table.FlexRender`. |
| Manual setup | [React quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md) | partial | Existing app is assumed; no complete framework-neutral file tree exists. |
| Core configuration and mental model | [row models](row-models-features-and-server-side.md) | ready | Data, columns, state, features, and row pipeline are covered. |
| Minimal runnable example | [React quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md) | partial | The component is complete, but the host React app and scripts are external. |
| Verification / build | [React quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md) | partial | Observable checks are stated; official universal command is absent. |
| Common setup mistakes | [React quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md) | ready | Stable references, feature registration, rendering, and controlled state are covered. |

Greenfield bootstrap is **partial**, not ready, because project creation,
complete adapter files, and an official build command are framework-owned.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Greenfield setup | partial | [installation](installation-and-package-choice.md), [React quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md) |
| Common feature work | partial | [row models](row-models-features-and-server-side.md) covers the feature model, but feature-specific handlers and state contracts remain deferred. |
| Debugging | partial | Failure modes are indexed; no dedicated troubleshooting section exists. |
| V8 to v9 migration | partial for seven adapters | [migration map](v8-to-v9-migration-and-api-map.md) identifies the first-party guides but does not retain their instructions. |
| Alpine/Ember/Octane/Vanilla migration | blocked | First-party migration pages are not present. |
| Production and build concerns | partial | Server/client decisions and performance cautions are covered; app build is external. |

## Substantive section map

| Source section | Memory page or status |
|---|---|
| Overview, installation, devtools, agent skills | [installation](installation-and-package-choice.md) |
| Framework quick starts | [React quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md); other adapters deferred |
| Data, columns, tables, rows, cells, headers | Core concepts in [row models](row-models-features-and-server-side.md); React rendering in the [adapter quick start](../../tanstack-react-table/9.2.4/quick-start-and-table-state.md); detailed APIs deferred |
| Features and row models | [row models](row-models-features-and-server-side.md) |
| Client/server and worker processing | [row models](row-models-features-and-server-side.md) |
| Filtering, sorting, grouping, pagination | [row models](row-models-features-and-server-side.md); individual APIs deferred |
| Selection, pinning, sizing, visibility | mapped but deferred to a later feature batch |
| Custom features and composable tables | mapped in [row models](row-models-features-and-server-side.md); detail deferred |
| Virtualization | interaction summarized; adapter detail deferred |
| V9 migrations and legacy bridge | [migration map](v8-to-v9-migration-and-api-map.md) |
| Core and adapter API | [migration/API map](v8-to-v9-migration-and-api-map.md) |
| 389 examples | discovered; not copied in this bounded batch |

## Recipes, warnings, and troubleshooting

| Category | Coverage |
|---|---|
| Stable data and column references | indexed |
| Controlled versus internal state | indexed |
| Client versus server processing | indexed |
| Row identity and selection stability | indexed |
| Virtualization interaction | indexed at decision level |
| Fuzzy filtering | identified; implementation deferred |
| Dedicated troubleshooting guide | not present |
| Accessibility recipe | not present as a complete Table-owned solution |
| Performance thresholds | not present; docs require representative testing |

## Version and package mismatches

- Core and adapters are `9.2.4`; devtools are `9.2.0`.
- `@tanstack/match-sorter-utils` is `9.1.2`.
- Cached npm/search pages may still display stable v8.
- Cross-repository examples can pin Table v8 and must retain their manifests.

## Bounded stopping point

This draft batch indexes core package decisions, row-model fundamentals,
server/client processing, migration discovery, and the API map. React-specific
bootstrap and rendering live under `@tanstack/react-table@9.2.4`. It defers
per-feature API pages, complete apps, devtools operation, accessibility recipes,
and the example corpus. No catalog entry is created.
