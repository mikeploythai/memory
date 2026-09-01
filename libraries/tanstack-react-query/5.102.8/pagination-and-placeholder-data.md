---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "pagination and placeholder query data"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/paginated-queries.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Pagination and placeholder query data

Page number, cursor, filters, and page size belong in the query key because they change the requested result. Each page is then cached independently. A straightforward page change therefore moves to another query and can enter a pending state even when the previous page remains in cache.

`placeholderData` can keep a prior successful value visible while the new key fetches. The helper used for previous data marks the result as placeholder data, allowing the UI to retain its layout and disable forward navigation until the new response confirms another page. Placeholder data is not written into the cache as real data for the new key.

Do not confuse placeholder data with `initialData`. Initial data seeds the cache and participates in freshness timestamps. Placeholder data is an observer-level display value used while the actual query has no data. Use initial data only when the supplied value is valid cache data for that exact key.

Prefetch the next page when its key is predictable and the current response indicates it exists. Prefetching uses normal stale-time rules, so it should share the same query options as the consuming hook. Avoid prefetching an unbounded number of pages.

When page results can change after mutations, invalidate the affected page family or update specific keys. A key that omits filters or page size can collide with a different view. A UI that displays placeholder data should also surface background errors appropriately; preserving the old page must not silently imply the new page loaded successfully.

Use an infinite query rather than numbered-query pagination when pages form one growing list with `fetchNextPage` semantics.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/paginated-queries.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/placeholder-query-data.md
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/examples/react/pagination


