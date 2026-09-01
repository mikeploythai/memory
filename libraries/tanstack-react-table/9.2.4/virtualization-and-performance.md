---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "virtualization and performance"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/virtualization.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Virtualization and performance

Virtualization is a rendering strategy supplied by another library, not a TanStack Table feature. The official React examples use TanStack Virtual for rows, columns, both axes, dynamic row heights, and infinite scrolling. Table still creates and processes the loaded row model; the virtualizer chooses which rendered elements enter the DOM.

Use virtualization when rendering many loaded rows or columns is the bottleneck. It does not reduce network transfer, retained data, filtering, sorting, grouping, or aggregation work. If the complete dataset is too large to load, use server-side operations or incremental fetching first, then virtualize the loaded window if necessary.

Fixed-size rows are simplest and cheapest. Dynamic heights require measurement and enough overscan to avoid blank regions while measurements settle. Sticky headers and semantic table markup need deliberate CSS because transformed virtual rows can conflict with normal table layout. Keep the scroll container and measurement strategy stable.

Avoid rerendering the full table body on every scroll and avoid expensive cell renderers in very large lists. Column resizing and virtual scrolling can multiply update cost, so profile them together. Experimental examples update scroll-position-only styles outside React. Keep that imperative path limited to transforms, spacer sizes, and body dimensions; do not use it for business data, table state, sorting, filters, or cell values.

For infinite remote data, server sorting or filtering must replace the fetched dataset rather than reorder only loaded rows. Reset the virtualizer to the top after such a replacement. Choose an experimental example only after profiling proves the normal React implementation insufficient.

## Sources

- [Virtualization guide](https://tanstack.com/table/latest/docs/framework/react/guide/virtualization.md)
- [Virtualized rows example](https://tanstack.com/table/latest/docs/framework/react/examples/virtualized-rows.md)
- [Virtualized columns example](https://tanstack.com/table/latest/docs/framework/react/examples/virtualized-columns.md)
- [Virtualized infinite-scrolling example](https://tanstack.com/table/latest/docs/framework/react/examples/virtualized-infinite-scrolling.md)


