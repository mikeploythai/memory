---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "render optimization and Suspense"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/render-optimizations.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Render optimization and Suspense

TanStack Query uses structural sharing to retain references for unchanged JSON-compatible result subtrees. The top-level hook result object is not referentially stable, but properties such as `data` remain stable when their content has not changed. Memoize or derive values from stable properties, not from the entire hook result object.

Tracked properties limit notifications to fields the component actually reads. Object rest destructuring reads every property and defeats this optimization. The ESLint plugin can catch that pattern. `select` transforms or narrows observed data and can prevent unrelated changes from rerendering a component. Keep selector references stable when their cost matters, and remember that `select` runs on successful cached data rather than replacing query-function error handling.

Suspense query hooks throw a promise while data is unavailable and throw errors to an error boundary under the documented reset rules. They do not expose the same optional-data state as ordinary hooks because resolved rendering assumes data exists. Place a Suspense boundary for loading UI and a Query error-reset boundary around recoverable query errors.

Multiple suspense queries declared sequentially can create a waterfall because the first suspension prevents later hooks from running. Use the supported suspense multi-query API or separate components/boundaries when requests are independent. Cancellation is not supported identically for every suspense path, so do not assume unmounting always aborts work.

Suspense changes rendering control flow, not cache identity or freshness. Stable keys, stale time, prefetching, and invalidation still apply. Avoid toggling a suspense query off by removing required variables without restructuring the component; dependent suspense work is often clearer behind a conditional child boundary.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/render-optimizations.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/suspense.md
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/examples/react/suspense


