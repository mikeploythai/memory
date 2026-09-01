---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "infinite queries and page management"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/infinite-queries.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Infinite queries and page management

An infinite query stores one cache entry containing parallel `pages` and `pageParams` arrays. The query function receives a `pageParam`; `initialPageParam` supplies the first value, and `getNextPageParam` or `getPreviousPageParam` derives another value from the current result. The UI calls `fetchNextPage` or `fetchPreviousPage` and checks the corresponding availability and fetching flags.

Do not reuse the same query key for `useQuery` and `useInfiniteQuery`. Their cached data shapes differ. Filters that define the whole list belong in the key, while the cursor for each fetched page belongs in `pageParams`.

Only one fetch should normally update an infinite-query cache entry at a time. Starting another page fetch while a background refetch is active can overwrite work unless the requested cancellation behavior is deliberate. Guard load-more triggers with the provided fetching state and avoid calling `fetchNextPage` directly as an event object handler that accidentally passes an argument as options.

When an infinite query becomes stale, pages are refetched in sequence from the beginning. This protects cursor consistency when earlier data changed. Selectively keeping later pages while refreshing only an earlier cursor can create duplicates or gaps. `maxPages` can bound retained pages when both next- and previous-page parameters are configured correctly.

Manual cache edits must preserve both `pages` and `pageParams` and must be immutable. Reversing display order, removing an item, or retaining only the first page should return a new structure with those arrays still aligned.

Use the exact-version example for load-more behavior and the bounded-page example when memory growth matters; adapt its API contract rather than copying endpoint-specific code.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/infinite-queries.md
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/examples/react/load-more-infinite-scroll
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/examples/react/infinite-query-with-max-pages


