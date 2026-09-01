---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "testing React Query behavior"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/testing.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Testing React Query behavior

Create a fresh `QueryClient` for each test and wrap the tested hook or component in its provider. A shared client leaks cache state, retry timers, mutation state, and defaults between tests. If tests run in parallel, isolation is required rather than merely clearing one global client after each test.

Disable retries for tests that assert errors unless retry behavior is the subject of the test. Default query retries delay failure assertions and can make tests appear hung. Set test defaults on the client used by the wrapper, not in production configuration. Configure garbage collection deliberately when a test runner warns about outstanding timers.

Mock the network boundary rather than the hook implementation. Wait for observable success, error, or fetched data using the testing library's asynchronous utilities. React 18 wait semantics require the assertion inside the waiting callback. Do not assert immediately after render when a query promise has not settled.

Infinite-query tests should model page parameters and server responses for each cursor. Test that `fetchNextPage` appends the expected page and that availability flags change. For request mocking, keep handlers deterministic and reset them between cases.

Cache behavior deserves direct tests only when the application relies on it. Verify key separation, invalidation, optimistic rollback, or prefetch reuse through public Query APIs and rendered outcomes. Avoid reaching into undocumented cache internals.

For SSR tests, create request-scoped clients, dehydrate, serialize, and hydrate as production does. A component test that begins with a prefilled browser cache does not verify server isolation or serialization safety. When testing errors, reset the Query error boundary before retrying so the rejected state does not immediately rethrow.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/testing.md


