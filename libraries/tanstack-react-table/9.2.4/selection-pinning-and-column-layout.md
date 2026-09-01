---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "selection pinning and column layout"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/cell-selection.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Selection, pinning, and column layout

Row selection stores row IDs, not row objects. Supply `getRowId` when indexes are not durable, especially with remote pagination or reordered data. Selection can be limited per row and can include rows not present in the current page when state is controlled externally. Rendering should derive checkbox state from table APIs rather than mutate the original data.

Cell selection adds spreadsheet-style ranges. Its interaction handlers need a clear keyboard and pointer policy, and the selected rectangle should be represented accessibly in application markup. Cell spanning merges adjacent body cells across rows or columns; spans change layout, not the underlying row model, so sorting and filtering still operate on source rows.

Column order, visibility, sizing, resizing, and pinning are separate state slices. Keep one owner for each. Ordering normally applies to leaf columns; grouped headers are derived from the resulting layout. Pinning divides visible columns into left, center, and right regions. Sticky and split-table implementations are application rendering choices demonstrated by separate examples.

Sizing is numeric state; resizing adds pointer interactions and a resize mode. Continuous `onChange` resizing can update frequently, so expensive cell trees may need memoized rendering or CSS variables. The performant-resizing example is the reference when drag performance degrades. Avoid recalculating all style objects in every cell on every pointer move.

Visibility controls which columns participate in visible-column APIs. Do not render the complete column list and hide cells only with CSS, because header alignment and feature APIs expect the visibility state to be authoritative.

## Sources

- [Cell selection](https://tanstack.com/table/latest/docs/framework/react/guide/cell-selection.md)
- [Cell spanning](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/cell-spanning.md)
- [Row selection](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/row-selection.md)
- [Column pinning](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/column-pinning.md)
- [Column resizing](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/column-resizing.md)
- [Column visibility](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/column-visibility.md)


