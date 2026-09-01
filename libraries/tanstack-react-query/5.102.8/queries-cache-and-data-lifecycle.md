---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "queries, cache, and data lifecycle"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/queries.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-query@5.102.8; commit 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Queries, cache, and data lifecycle

A query combines a serializable key with an asynchronous function. The key
identifies cached data and must include every variable used by the query
function that changes the result.

## Query keys and functions

```tsx
import { useQuery } from '@tanstack/react-query'

function Todo({ todoId }: { todoId: number }) {
  const todo = useQuery({
    queryKey: ['todo', todoId],
    queryFn: ({ signal }) =>
      fetch(`/api/todos/${todoId}`, { signal }).then((response) => {
        if (!response.ok) throw new Error('Unable to load todo')
        return response.json() as Promise<{ id: number; title: string }>
      }),
  })

  if (todo.isPending) return <p>Loading...</p>
  if (todo.isError) return <p>{todo.error.message}</p>
  return <p>{todo.data.title}</p>
}
```

Query keys are hashed deterministically. Object property order does not create
a different cache entry, but array item order does. Do not reuse one key for
incompatible finite and infinite query shapes.

## Dependent and parallel work

Use `enabled` when one query depends on data from another. Independent queries
can run in parallel through sibling hooks or `useQueries`. Avoid serial
waterfalls when the inputs are already known.

```tsx
const user = useQuery({
  queryKey: ['user', email],
  queryFn: () => getUser(email),
})

const projects = useQuery({
  queryKey: ['projects', user.data?.id],
  queryFn: () => getProjects(user.data!.id),
  enabled: Boolean(user.data?.id),
})
```

## Pagination and infinite queries

Paginated queries place the page or cursor in the key. Placeholder data can
retain the previous result while the next page loads. Infinite queries keep a
`pages` array and matching `pageParams`; `getNextPageParam` controls progress.

Set `maxPages` when an unbounded infinite result would retain too much data.
Only call `fetchNextPage` when another request is not already in progress unless
the intended cancellation behavior is explicit.

## Cancellation

Query supplies an `AbortSignal` to the query function. Pass it to `fetch` or a
compatible client so unused work can stop. Ignoring the signal leaves the
underlying request running even if Query no longer needs its result.

## Cache lifecycle

1. The first observer starts the query unless usable data already exists.
2. The result is stored under the query key.
3. Additional observers share the cache entry.
4. Stale queries may refetch under configured triggers.
5. A query becomes inactive after its last observer unmounts.
6. Inactive data is removed after `gcTime` unless reused first.

## Prefetching and routers

`queryClient.prefetchQuery` warms the cache without returning data.
`ensureQueryData` returns cached or fetched data and is suitable for router
loaders. Ensure the loader and component use the same key and query function.

```ts
const todoOptions = (id: number) => ({
  queryKey: ['todo', id] as const,
  queryFn: () => getTodo(id),
})

await queryClient.ensureQueryData(todoOptions(todoId))
```

## Failure modes

- A missing key dependency serves one variable's data for another variable.
- A query function returning `undefined` violates the documented data contract.
- Disabling every query replaces declarative dependencies with imperative
  refetch orchestration.
- Global `staleTime: Infinity` can hide invalidation mistakes.
- Sequential component-level fetching can create avoidable request waterfalls.

## Sources

- https://tanstack.com/query/latest/docs/framework/react/guides/query-keys.md
- https://tanstack.com/query/latest/docs/framework/react/guides/query-functions.md
- https://tanstack.com/query/latest/docs/framework/react/guides/dependent-queries.md
- https://tanstack.com/query/latest/docs/framework/react/guides/infinite-queries.md
- https://tanstack.com/query/latest/docs/framework/react/guides/query-cancellation.md
- https://tanstack.com/query/latest/docs/framework/react/guides/prefetching.md
