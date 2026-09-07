---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "coverage map"
source: "https://tanstack.com/table/latest/llms.txt"
retrieved_at: "2026-09-07"
source_ref: "@tanstack/react-table@9.2.4 (d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6)"
---

# TanStack React Table 9.2.4 coverage map

This adapter-specific map complements the `@tanstack/table-core@9.2.4`
coverage map and keeps React readiness claims scoped to the retained component.

## First-party indices and refs inspected

| Source | Result |
|---|---|
| https://tanstack.com/table/latest/llms.txt | Moving index used to inventory React setup, guides, migrations, and APIs |
| https://github.com/TanStack/table/tree/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react | Immutable React documentation tree |

## Bootstrap chain

| Requirement | Status | Evidence or gap |
|---|---|---|
| Package choice and prerequisites | partial | Core [installation](../../tanstack-table-core/9.2.4/installation-and-package-choice.md) identifies the React package and independent devtools versions; host runtime/tooling ranges are external |
| Project creation | not applicable | Table assumes an existing React application |
| Installation | ready | Exact `@tanstack/react-table@9.2.4` command is indexed in the core installation page |
| Required files and configuration | partial | The complete component declares features, data, and columns; host entry wiring is external |
| Getting started and mental model | ready | [React quick start](quick-start-and-table-state.md) covers feature registration, stable inputs, rendering, and state ownership |
| Minimal runnable application | partial | The typed table component is complete, but the React host and scripts are absent |
| Run/build verification | partial | Observable row and type checks are stated; the host's build command is external |
| Setup mistakes and version caveats | ready | V8/v9 API separation, stable references, controlled state, rendering ownership, and devtools versioning are covered |

Greenfield React application setup is partial. A basic typed table can be added
to an existing compatible React application, but this corpus does not supply
the host project or build proof.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Greenfield React application | partial | Project creation, entry files, and build scripts are external |
| Add a typed core-feature table | partial | [React quick start](quick-start-and-table-state.md); host verification remains external |
| Add sorting, filtering, pagination, grouping, or selection | partial | Core feature model is indexed; feature-specific React handlers and state contracts are deferred |
| Debug rendering or state loops | partial | Stable-reference and controlled-state failure modes are indexed; no troubleshooting corpus exists |
| V8 to v9 migration | partial | Core migration map identifies the guide, but a verified React migration is not retained |
| Production/build concerns | partial | Rendering ownership and server/client choices are mapped; application build is external |

## Source coverage

| Source area | Status | Memory page or gap |
|---|---|---|
| Installation and package/version choice | indexed | Core [installation and package choice](../../tanstack-table-core/9.2.4/installation-and-package-choice.md) |
| React quick start, rendering, stable inputs, and table state | indexed, bounded | [React quick start and table state](quick-start-and-table-state.md) |
| Feature guides | deferred | Sorting, filtering, pagination, grouping, expansion, selection, pinning, sizing, ordering, and visibility need substantive adapter pages |
| React examples | deferred | The example corpus is not mirrored in this bounded index |
| React API and devtools | deferred | Exact generated signatures and devtools configuration are not retained here |
| Migration | partial | Core migration inventory exists; end-to-end React instructions remain deferred |

## Patterns, warnings, and stopping point

The retained page preserves the v9 `tableFeatures` and `useTable` model,
feature-aware column types, `table.FlexRender`, stable input references, and
controlled-state cautions. This audit adds the missing adapter coverage map
without expanding feature-specific implementation coverage.

## Sources

- https://github.com/TanStack/table/tree/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react

