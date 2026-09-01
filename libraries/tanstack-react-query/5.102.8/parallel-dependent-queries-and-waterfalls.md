---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "parallel queries, dependent queries, and request waterfalls"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/parallel-queries.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Parallel queries, dependent queries, and request waterfalls

Independent queries should begin together. Multiple `useQuery` calls next to one another run in parallel in ordinary rendering. For a dynamic number of queries, `useQueries` accepts an array of query definitions and returns corresponding results. In Suspense mode, placing multiple suspense hooks in one component can suspend on the first query before later hooks start; use the supported suspense multi-query API or split boundaries when parallel start time matters.

Dependent queries use `enabled` to wait for a value produced by another query. This is correct when the second request truly cannot be formed without the first result. It also creates a request waterfall: the second network round trip cannot begin until the first has completed. The total latency is roughly the sum of the dependent requests.

Before accepting a waterfall, consider whether the backend can expose a combined endpoint, whether both inputs already exist at a higher route level, or whether a router loader can begin independent work earlier. Moving a dependent hook into a child component does not remove the dependency. Prefetching can hide some latency only if the needed key is known in advance.

Waterfalls can also arise from code splitting and nested rendering: the application downloads a component before discovering its query, or a parent renders before a child can request data. Route-level prefetching and server-side aggregation can flatten these chains.

Do not bypass `enabled` by calling a query function manually from an effect. That loses shared caching and cancellation while retaining the same dependency. Model the dependency in the key and enabled condition, and represent the waiting state separately from active loading.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/parallel-queries.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/dependent-queries.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/request-waterfalls.md


