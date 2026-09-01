---
library: "@tanstack/table-core"
version: "9.2.4"
topic: "v8 to v9 migration and API map"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/migrating.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/table-core@9.2.4 (d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6)"
---

# V8 to v9 migration and API map

TanStack Table v9 is a stable major release. Treat migration as a source and
target version task: keep v8 behavior available while adopting the v9 adapter,
feature registration, and state model deliberately.

This page is a migration index, not a retained migration procedure. It records
where first-party guides exist and the checks a migration needs, but completing
an adapter migration still requires that adapter's unindexed guide. Migration
readiness is therefore partial for the seven adapters listed below.

## Migration sequence

1. Pin the current v8 package and capture passing behavior.
2. Install the matching v9 adapter at `9.2.4`.
3. Open the migration guide for that framework.
4. Update table creation, column helpers, feature registration, and rendering.
5. Reconcile controlled state with the v9 TanStack Store model.
6. Verify sorting, filtering, pagination, selection, and custom features.
7. Remove compatibility code only after equivalent behavior passes.

React users who need an incremental path can consult the documented
`useLegacyTable` guide. It is a bridge, not evidence that all v8 code is natively
v9-compatible.

## Migration pages

- React: https://tanstack.com/table/latest/docs/framework/react/guide/migrating.md
- Preact: https://tanstack.com/table/latest/docs/framework/preact/guide/migrating.md
- Vue: https://tanstack.com/table/latest/docs/framework/vue/guide/migrating.md
- Angular: https://tanstack.com/table/latest/docs/framework/angular/guide/migrating.md
- Solid: https://tanstack.com/table/latest/docs/framework/solid/guide/migrating.md
- Svelte: https://tanstack.com/table/latest/docs/framework/svelte/guide/migrating.md
- Lit: https://tanstack.com/table/latest/docs/framework/lit/guide/migrating.md
- React legacy bridge: https://tanstack.com/table/latest/docs/framework/react/guide/use-legacy-table.md

There are no first-party v9 migration pages for Alpine, Ember, Octane, or the
Vanilla adapter in the pinned docs tree.

## Core API areas

The generated reference is larger than the hand-written guides. Its principal
areas are:

| Area | Representative contracts |
|---|---|
| Table | table options, instance, state, stores, feature map |
| Columns | definitions, helpers, accessors, visibility, ordering, sizing |
| Rows | row identity, row models, expansion, selection, pinning |
| Headers | header groups, headers, sizing and rendering context |
| Cells | cells, cell context, selection and spanning |
| Features | filter, sort, aggregate, paginate, group and state contracts |
| Functions | row-model creators, constructors, utilities |
| Static functions | generated instance operations by receiver and action |

Start at the [core reference index](https://tanstack.com/table/latest/docs/reference.md).
The llms index categorizes 266 API links plus the static-functions index. The
release tree contains 405 generated core-reference Markdown files and 286
static-function files.

## Adapter API areas

Framework references document adapter creation functions, rendering helpers,
subscription components, table contexts, and adapter-specific types. Use the
adapter reference rather than guessing a core function maps directly to every
framework.

Examples:

- https://tanstack.com/table/latest/docs/framework/react/reference/index.md
- https://tanstack.com/table/latest/docs/framework/angular/reference/index.md
- https://tanstack.com/table/latest/docs/framework/vue/reference/index.md

## Version checks

```sh
npm view @tanstack/table-core version
npm view @tanstack/react-table version
npm view @tanstack/react-table-devtools version
```

At retrieval these resolve to `9.2.4`, `9.2.4`, and `9.2.0`. Do not infer that
devtools share the core version.

## Gaps and cautions

- The generated API is authoritative for signatures but sparse on workflow.
- Migration coverage is framework-dependent and absent for four adapters.
- Search-engine caches may present v8 pages or versions as current.
- A successful type migration does not verify rendered semantics, keyboard
  behavior, or server-state coordination.

## Sources

- https://tanstack.com/table/latest/llms.txt
- https://tanstack.com/table/latest/docs/reference.md
- https://github.com/TanStack/table/tree/%40tanstack%2Ftable-core%409.2.4/docs/reference
- https://github.com/TanStack/table/releases/tag/%40tanstack%2Ftable-core%409.2.4
