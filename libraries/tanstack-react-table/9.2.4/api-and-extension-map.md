---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "API and extension map"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/reference/index.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# API and extension map

The generated core reference is the authoritative symbol directory for `@tanstack/table-core`; the React reference adds adapter types and functions. Use the reference when an implementation depends on an exact signature, option, state type, or return type. Use the guides for sequencing and ownership rules.

The main table group includes `Table`, `TableOptions`, `TableState`, `tableFeatures`, `constructTable`, and state/atom types. The React adapter group includes `useTable`, `createTableHook`, `Subscribe`, `FlexRender`, and application-specialized table/helper types. Column symbols include `ColumnDef`, accessor/display/group definitions, `createColumnHelper`, deep-key utilities, and column meta. Row-model symbols cover the core, filtered, sorted, grouped, expanded, paginated, and faceted factories.

Feature reference pages define each feature object plus its state and option types. Function registries expose the built-in filter, sort, and aggregation implementations. Import individual functions where tree shaking matters rather than spreading whole registries.

Custom plugins can add state, options, defaults, lifecycle behavior, and methods to table-related objects. Keep plugin configuration static and type it through the same feature set used by the table. Prefer a custom plugin when behavior genuinely belongs on table/row/column objects; ordinary application rendering or side effects can remain outside the table.

`createTableHook` builds a reusable, preconfigured table hook for shared defaults, components, or organizational conventions. Keep the composition layer narrow. It should not hide which features and state slices a concrete table owns, because that makes bundle contents and server/client processing boundaries harder to audit.

## Sources

- [Core API reference](https://tanstack.com/table/latest/docs/reference/index.md)
- [React API reference](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/reference/index.md)
- [Custom plugins guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/custom-features.md)
- [Composable tables guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/composable-tables.md)


