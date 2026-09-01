---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "rendering rows cells and headers"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/rows.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Rendering rows, cells, and headers

TanStack Table is headless. The table instance produces row, cell, column, header, and header-group objects; application code chooses the DOM, component library, semantics, styles, and interaction handlers. Render the current row model rather than the original data array so filtering, grouping, sorting, expansion, and pagination are reflected.

Rows expose their original record, computed values, visible cells, parent/subrow relationships, and feature-specific state. Use `getRowId` when the default index-based identity is not stable enough for selection, expansion, editing, or server requests. Cells connect a row and column. Their value APIs distinguish raw accessor values from rendered content, while their context object supplies the table, row, column, and cell to templates.

Header groups represent the nested column structure needed for multi-level headers. A header may be a placeholder created to preserve alignment. Check placeholder status before rendering content. Columns are configuration and state objects, not DOM columns; visible leaf columns are the usual basis for body layout.

Use the React adapter's FlexRender facility for column-defined header, cell, footer, and aggregated-cell templates. It resolves strings, JSX, and component callbacks using the correct context. Directly calling a component-valued template as a plain function can violate React's component and hook semantics.

Keep semantic table markup when it fits the interaction model. Virtualized or grid-like layouts may require CSS grid/flex positioning, but accessibility responsibilities remain with the application because the library supplies no markup. Table and column meta provide typed extension points for shared rendering services without modifying every column definition.

## Sources

- [Rows guide](https://tanstack.com/table/latest/docs/guide/rows.md)
- [Cells guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/cells.md)
- [Headers guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/headers.md)
- [Header groups guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/header-groups.md)
- [FlexRender guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/flex-render.md)

