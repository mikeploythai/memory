---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "sorting pagination and remote data"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/pagination.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# Sorting, pagination, and remote data

Sorting state is an ordered list of column identifiers and directions. Multi-sort preserves that order. Register the sorting feature for state and controls, then add a sorted row model for browser sorting or enable manual sorting when the server returns already-sorted rows. Custom sort functions should compare row values consistently and let the table apply direction; avoid embedding ascending/descending behavior twice.

Pagination state contains `pageIndex` and `pageSize`. Client pagination requires the paginated row model and works only on data already loaded. Manual pagination treats supplied rows as the current page. Provide `rowCount` or `pageCount` when known so navigation and page-count APIs remain accurate. Cursor-based APIs do not naturally map to a total page number; keep cursor history or use infinite loading rather than inventing offsets.

For remote tables, make every server-owned state slice part of both the query key and request. This includes sorting, filters, grouping, and pagination where applicable. Keep previous data only when that stale view is acceptable, and expose pending/refetch state in the UI. When filters or sorting change, reset page or cursor state deliberately. Fully manual pipelines may bypass the client row-model hooks that normally reset page index.

Do not sort a single server page in the browser unless page-local sorting is intentional and labeled. The same warning applies to filtering and aggregation. Use stable backend row IDs so selection and expansion survive page replacement.

Virtual infinite scrolling combines incremental fetching with a virtualizer. Server sorting must replace the fetched dataset and should scroll the virtualizer back to the beginning.

## Sources

- [Pagination guide](https://tanstack.com/table/latest/docs/framework/react/guide/pagination.md)
- [Sorting guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/sorting.md)
- [Client-side versus server-side guide](https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/client-side-vs-server-side.md)
- [TanStack Query example](https://tanstack.com/table/latest/docs/framework/react/examples/with-tanstack-query.md)


