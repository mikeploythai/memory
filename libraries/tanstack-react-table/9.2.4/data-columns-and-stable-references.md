---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "data columns and stable references"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/data.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Data, columns, and stable references

The row type should be defined before the table. TanStack Table infers column accessors, cell values, nested keys, and many feature APIs from that shape. `createColumnHelper<T>()` is the usual typed entry point. Accessor columns must produce primitive values if built-in sorting and filtering should work; accessors that return objects or arrays require matching custom functions. Display and group columns do not read a row value and therefore use explicit identifiers.

Data and column identity are part of the table's cache contract. A new `data` reference invalidates the core row model and rebuilds every row and cell. A new `columns` reference rebuilds column and header structures. Inline arrays and inline transformations such as `data.filter(...)` therefore cause repeated work. With auto-resetting features, an unstable data reference can also create a render loop: recomputation resets state, the state update renders again, and the next render creates another array.

Use module-scope constants, React state, `useMemo`, or a stable external store/query result. Memoize derived data separately from its source. Defining `features`, `columns`, and transformed data outside the `useTable` call is the portable pattern because it remains correct without React Compiler.

For dynamic schemas such as CSV uploads or configurable reports, generate column definitions at runtime but still memoize them against the schema, not every render. Choose stable unique column IDs. With deep object keys, confirm that the accessor path matches the row shape; array accessors use string keys such as `'1'`, not numeric keys.

## Sources

- [Data guide](https://tanstack.com/table/latest/docs/guide/data.md)
- [Column definitions guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/column-defs.md)
- [Type helpers guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/helpers.md)


