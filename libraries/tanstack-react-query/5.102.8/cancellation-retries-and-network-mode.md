---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "query cancellation, retries, and network modes"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/query-cancellation.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Query cancellation, retries, and network modes

Every query function receives an `AbortSignal`. Pass it through to `fetch`, Axios, or another supported client to make cancellation effective. If the signal is consumed and the query becomes obsolete, aborting rejects the request and restores query state to its prior value. If the signal is ignored, the promise can still resolve and populate the cache after the component unmounts.

Cancellation is useful for key changes, route changes, explicit cancel actions, and optimistic mutation preparation. Calling `cancelQueries` before a cache-level optimistic update prevents a background response from replacing the optimistic value. Distinguish cancellation from a server error in custom logging and UI.

Queries retry failed requests three times by default on the client, using exponential backoff capped by the configured delay. On the server, retries default to zero to avoid delaying rendering. Configure `retry` as a count or predicate when some errors are permanent. Do not retry authentication failures, validation failures, or non-idempotent work as if they were transient reads.

Network mode determines whether a query requires connectivity, runs regardless of online state, or begins and then pauses retry behavior while offline. A paused query is not the same as an idle disabled query. Use the fetch status alongside the query status to represent paused work accurately.

Offline mutation support needs persistence of both mutation state and a default mutation function that can resume after hydration. Network mode alone does not make an arbitrary side effect safely replayable. Design idempotency and conflict handling at the server boundary.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/query-cancellation.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/query-retries.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/network-mode.md


