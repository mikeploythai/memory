---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "queries, mutations, and invalidation"
source: "https://tanstack.com/query/latest/docs/framework/react/quick-start"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607; commit 2969edf; moving React v5 docs"
---

# Queries and invalidation with TanStack Query

TanStack Query v5 manages asynchronous server state through a shared `QueryClient`, declarative queries, mutations, and targeted invalidation.

## Installation

```sh
npm install @tanstack/react-query
```

React 18 or newer is required.

## Provide a client and read data

Create one client for the application and expose it with `QueryClientProvider`.

```tsx
import {
  QueryClient,
  QueryClientProvider,
  useQuery,
} from '@tanstack/react-query'

const queryClient = new QueryClient()

function Todos() {
  const query = useQuery({
    queryKey: ['todos'],
    queryFn: async () => {
      const response = await fetch('/api/todos')
      if (!response.ok) throw new Error('Unable to load todos')
      return response.json() as Promise<Array<{ id: number; title: string }>>
    },
  })

  if (query.isPending) return <p>Loading…</p>
  if (query.isError) return <p>{query.error.message}</p>

  return <ul>{query.data.map((todo) => <li key={todo.id}>{todo.title}</li>)}</ul>
}

export function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Todos />
    </QueryClientProvider>
  )
}
```

After a successful mutation, invalidate the affected key with `queryClient.invalidateQueries({ queryKey: ['todos'] })` so active queries can refetch.

## Notes

- Query keys identify cached data and should include every value used by the query function.
- The Fetch API does not reject HTTP error responses automatically; check `response.ok`.
- The source URL is moving React v5 documentation. The exact package release is recorded in `source_ref`.

## Sources

- https://tanstack.com/query/latest/docs/framework/react/installation
- https://github.com/TanStack/query/releases
