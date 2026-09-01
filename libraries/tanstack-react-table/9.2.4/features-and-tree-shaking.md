---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "features and tree shaking"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/features.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Features and tree shaking

TanStack Table v9 separates three kinds of configuration that are easy to confuse: features, row models, and function registries. Features add state, options, event handlers, and instance APIs. Row models perform client-side transformations such as filtering, grouping, sorting, expansion, pagination, and faceting. Function registries provide named filter, sort, and aggregation implementations.

Declare the static feature set with `tableFeatures()` outside the component when possible. A core-only table uses an empty object. Add individual feature objects for the capabilities the table needs. The helper validates relationships: for example, a sorted row model requires the sorting feature, while global filtering depends on column filtering. Omitting a feature removes its methods from the inferred API, which turns missing configuration into a type error.

A registered feature does not process rows by itself. For client-side processing, add its `create*RowModel()` factory. For server-side processing, keep the feature's state and controls, omit the client row model, and set the matching `manual*` option. Register named filter, sort, or aggregation functions only when columns refer to them by name; functions supplied directly to a column do not need registry entries.

`stockFeatures` spreads all optional stock features into a table. It is reasonable for prototypes or compatibility layers that truly need nearly everything, but it includes all feature code and weakens tree shaking. It also does not add row models or function registries. Prefer named feature imports in production and keep the declaration stable so shared helpers can reuse its inferred type.

## Sources

- [Features guide](https://tanstack.com/table/latest/docs/guide/features.md)
- [Core API index](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/reference/index.md)


