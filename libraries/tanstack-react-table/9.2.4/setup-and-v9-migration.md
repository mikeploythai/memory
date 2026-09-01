---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "setup and v9 migration"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/migrating.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Setup and migration to TanStack Table v9

Install `@tanstack/react-table` and create tables with the v9 `useTable` API. A table requires `data`, `columns`, and a static `features` object created with `tableFeatures()`. The feature declaration is not optional boilerplate: it determines which optional capabilities are bundled and which methods TypeScript exposes on table, row, column, header, and cell objects.

The v9 API is a substantial change from v8. The primary hook is `useTable`, not `useReactTable`. Row-model factories use `create*` names, and feature objects must be registered explicitly. Rendering uses the React adapter's `table.FlexRender` or exported render helper. Existing v8-style code can move incrementally through `useLegacyTable`, but that compatibility API should be treated as a migration bridge rather than the target architecture.

Start a migration by identifying every v8 feature used by the table, then register the equivalent v9 feature and row model deliberately. Do not mechanically copy every stock feature: importing `stockFeatures` increases the bundle and still does not add client-side row models or function registries. Convert state ownership one slice at a time, especially pagination, filters, sorting, grouping, and selection.

Keep column definitions, feature configuration, and data references stable. V9's React Compiler support can stabilize values in successfully compiled components, but code that must also run without the compiler still needs module-scope constants, `useMemo`, state, or another stable source.

## Sources

- [React quick start](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/quick-start.md)
- [Migrating to v9](https://tanstack.com/table/latest/docs/framework/react/guide/migrating.md)
- [useLegacyTable guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/use-legacy-table.md)


