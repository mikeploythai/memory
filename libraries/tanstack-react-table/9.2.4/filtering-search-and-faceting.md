---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "filtering search and faceting"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/column-filtering.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Filtering, search, and faceting

Column filtering, global filtering, fuzzy matching, and faceting are related but separate features. Register column filtering before global filtering because global filtering builds on it. Add a filtered row model only when filtering happens in the browser; use manual filtering when the server owns the full dataset.

Each filter stores a column identifier and filter value. A filter function decides whether a row passes and can attach filter metadata used by later steps. Built-in functions cover common string, equality, array, and range cases. Register a named function when a column refers to it by key, or supply a function directly in the column definition. Accessor values should be primitive or paired with a custom filter that understands their shape.

Global filtering considers eligible columns across a row. Control which columns participate instead of treating every displayed value as searchable. For remote data, serialize the global value into the request and query key; a client global filter over one server page is not a dataset-wide search.

Fuzzy filtering is a recipe, not a separate stock feature. It combines filtering metadata with a rank-aware sort so close matches appear first. Preserve the rank metadata if sorting should use it.

Faceting derives unique values, counts, or numeric ranges for filter UIs. Client faceting uses faceted row-model factories. Server faceting uses custom factories that return server-provided results; enabling manual filtering alone does not manufacture facet values. Bucketed and high-cardinality facets should be bounded so the UI and network do not attempt to enumerate an unbounded domain.

## Sources

- [Column filtering](https://tanstack.com/table/latest/docs/framework/react/guide/column-filtering.md)
- [Global filtering](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/global-filtering.md)
- [Fuzzy filtering](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/fuzzy-filtering.md)
- [Column faceting](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/column-faceting.md)


