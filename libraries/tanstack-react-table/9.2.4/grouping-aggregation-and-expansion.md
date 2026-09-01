---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "grouping aggregation and expansion"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/grouping.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Grouping, aggregation, and expansion

Grouping transforms flat rows into a hierarchy based on one or more column values. Register the grouping feature and grouped row model for client processing. Grouping state records the ordered grouping columns, which matters because each additional column creates another level. Grouped cells, aggregated cells, and placeholder cells need distinct rendering paths.

Aggregation computes values over a row set. A column can choose a built-in aggregation or a registered custom implementation. Aggregation functions should return a value that the column's `aggregatedCell` renderer understands; it may differ from the leaf accessor value. V9 exposes richer aggregation context for calculations that need grouped, root, or custom row sets. Keep expensive aggregation work pure and deterministic because row-model recomputation may call it many times.

Expansion controls which hierarchical rows reveal subrows or custom detail content. Nested data normally comes from `getSubRows`. A subcomponent/details row is an application rendering pattern rather than data grouping, but it can share expansion state. Stable row IDs are essential if expansion must survive filtering, sorting, pagination, or remote requests.

These operations belong to one processing boundary. If the server supplies only a page, client grouping and aggregation operate only on that page. Dataset-wide totals or group counts must come from the server. In manual mode, the table still coordinates state and rendering, but the backend must return the grouped or aggregated shape expected by the UI.

Aggregation and expansion interact with pagination. Decide whether expansion happens before or after paging and verify the selected row model matches that expectation. Large deep trees may also need virtualization, but virtualization does not reduce grouping or aggregation work.

## Sources

- [Grouping guide](https://tanstack.com/table/latest/docs/framework/react/guide/grouping.md)
- [Aggregation guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/aggregation.md)
- [Expanding guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/expanding.md)


