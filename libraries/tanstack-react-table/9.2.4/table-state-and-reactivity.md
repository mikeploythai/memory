---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "table state and React reactivity"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/table-state.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Table state and React reactivity

TanStack Table can own all state internally. Most tables should begin there. Use `initialState` when only the starting value needs customization. Hoist a slice only when application code needs to read, persist, synchronize, or send it elsewhere, such as putting pagination and sorting in a query key.

V9 state is atomic. React can subscribe to the whole selected state, a subset, or one atom. `useTable` supports selectors, while `table.Subscribe` moves a reactive boundary lower in the tree. Reach for narrow subscriptions after correctness is established or profiling shows that broad table renders are expensive.

Give each state slice one owner. For a slice such as pagination, prefer exactly one of `initialState.pagination`, `atoms.pagination`, or `state.pagination`. External atoms take precedence over external state, and external state synchronizes into the internal base atom. When an external atom owns a slice, table APIs write to that atom directly; a duplicate `onPaginationChange` callback is not required. Slice-specific reset methods use the feature's updater, while `table.reset()` resets internal base atoms and is not the primary reset mechanism for externally owned state.

React Compiler supports v9, but stable table objects create one sharp edge. A nested component may receive an unchanged `row`, `cell`, or `header` object while methods on that object return changing state. The compiler may reuse the old component output. Put `Subscribe` inside the component that reads the state, or pass the selected primitive value as a prop. Subscribing outside the child and ignoring the selected value does not guarantee a fresh method call.

## Sources

- [React table-state guide](https://tanstack.com/table/latest/docs/framework/react/guide/table-state.md)
- [React Compiler guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/react-compiler.md)
- [Table instance guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/tables.md)


