---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "row models and server processing"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/client-side-vs-server-side.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Row models and server processing

Row models form an ordered synchronous pipeline over data already in memory. The core model creates rows; optional models can then filter, group, sort, expand, paginate, and facet them. Each model requires its matching feature registration. Table instance methods expose both processed models and `getPre*RowModel` variants used before a processing step.

Choose one dataset-wide processing boundary. If the browser holds the complete result set, client-side row models provide immediate filtering, grouping, sorting, aggregation, and pagination. If the server sends only a page or window, it should usually own every operation that must apply to the full result. Sorting a server-paginated page in the browser sorts only that page; filtering it cannot find matches outside the loaded rows.

`manual*` means “the supplied data is already processed.” It does not fetch data or run backend logic. Keep feature state and controls enabled, omit the client row model, set the relevant manual options, and make the controlled state part of the request contract. Manual pagination also needs `rowCount` or `pageCount` when known. Use a stable backend identifier through `getRowId`; page-relative indexes cannot preserve selection or expansion across responses.

TanStack Query is an optional coordinator for request state and caching, not a hidden Table dependency. Include every server-owned filter, sort, group, and page value in the query key and request. Reset dependent state deliberately when manual processing bypasses row-model auto-reset hooks.

Worker row models are experimental. Use them only after profiling shows synchronous processing is the bottleneck, and treat stale worker results and serialization cost as part of the design.

## Sources

- [Client-side versus server-side guide](https://tanstack.com/table/latest/docs/guide/client-side-vs-server-side.md)
- [Row-model guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/row-models.md)
- [Worker row-model guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/worker-row-models.md)
- [TanStack Query integration example](https://tanstack.com/table/latest/docs/framework/react/examples/with-tanstack-query.md)


