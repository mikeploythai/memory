---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "bootstrap, QueryClient, and defaults"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/installation.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-query@5.102.8; commit 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Bootstrap, QueryClient, and defaults

TanStack Query manages asynchronous server state. It does not create or build a
React application, so the official bootstrap assumes an existing React host.

## Requirements and installation

- React 18 or later; ReactDOM and React Native are supported hosts.
- Documented browser floor: Chrome 91, Firefox 90, Edge 91, Safari/iOS 15,
  and Opera 77.
- Older environments may need polyfills and application-side transpilation.

```sh
npm i @tanstack/react-query
npm i -D @tanstack/eslint-plugin-query
```

The ESLint plugin is recommended rather than required.

## Create and provide a client

Create one `QueryClient` for the client application and provide it above every
component that calls Query hooks.

```tsx
import {
  QueryClient,
  QueryClientProvider,
  useQuery,
} from '@tanstack/react-query'

const queryClient = new QueryClient()

export function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Repository />
    </QueryClientProvider>
  )
}

function Repository() {
  const query = useQuery({
    queryKey: ['repository', 'TanStack/query'],
    queryFn: () =>
      fetch('https://api.github.com/repos/TanStack/query').then((response) => {
        if (!response.ok) throw new Error('Request failed')
        return response.json() as Promise<{ name: string }>
      }),
  })

  if (query.isPending) return <p>Loading...</p>
  if (query.isError) return <p>{query.error.message}</p>
  return <h1>{query.data.name}</h1>
}
```

This example adds an explicit HTTP-status check; `fetch` does not reject merely
because a server returned a 4xx or 5xx response.

## Important defaults

- Cached query data is stale by default.
- Stale active queries may refetch when a new instance mounts, the window
  regains focus, or the network reconnects.
- Failed queries retry before surfacing an error under the default client
  configuration.
- Inactive queries remain cached until their garbage-collection interval ends.
- Query results use structural sharing where possible to preserve stable value
  references.

Set `staleTime`, refetch policy, retry policy, and `gcTime` based on data
semantics rather than disabling defaults globally to quiet unexpected requests.

```ts
const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 60_000,
      retry: 2,
    },
  },
})
```

## Verification and bootstrap gap

Render the host application and observe `Loading...`, then the repository name
or the error state. Query Devtools can provide an additional development-time
check, but it is a separate package.

The official quick start assumes application functions such as `getTodos` and
the host renderer already exist. It gives no project-creation, `dev`, or
`build` command. Greenfield readiness therefore remains partial until paired
with an official host-framework bootstrap or a fully pinned example project.

## Sources

- https://tanstack.com/query/latest/docs/framework/react/overview.md
- https://tanstack.com/query/latest/docs/framework/react/quick-start.md
- https://tanstack.com/query/latest/docs/framework/react/guides/important-defaults.md
- https://tanstack.com/query/latest/docs/framework/react/devtools.md
