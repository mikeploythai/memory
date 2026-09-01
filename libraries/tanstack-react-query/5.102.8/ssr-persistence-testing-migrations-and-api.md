---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "SSR, persistence, testing, migrations, and API"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/ssr.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-query@5.102.8; commit 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# SSR, persistence, testing, migrations, and API

This page maps cross-cutting operational material. It does not replace the
individual generated API pages.

## Server rendering and hydration

Create a fresh `QueryClient` per server request. Prefetch required queries,
dehydrate the cache, serialize the state through the framework safely, and
hydrate it under the matching client provider.

```tsx
import {
  HydrationBoundary,
  QueryClient,
  dehydrate,
} from '@tanstack/react-query'

const queryClient = new QueryClient()
await queryClient.prefetchQuery({
  queryKey: ['posts'],
  queryFn: getPosts,
})

const dehydratedState = dehydrate(queryClient)

<HydrationBoundary state={dehydratedState}>
  <Posts />
</HydrationBoundary>
```

The surrounding framework determines how the state crosses the network. A
module-level QueryClient on the server can share cached data between users.
Advanced SSR and streaming add framework-specific timing and ownership rules.

## Persistence

The React plugin pages cover:

- `persistQueryClient`
- `createSyncStoragePersister`
- `createAsyncStoragePersister`
- Experimental `broadcastQueryClient`
- Experimental `createPersister`

Persistence needs a cache lifetime compatible with the persisted maximum age.
Use a version or buster when stored schemas change. Browser storage is not a
safe place for secrets, and persistence is not a replacement for server truth.

## Testing

Create an isolated QueryClient per test and wrap the tested hook or component
with its provider. Disable retries or use deterministic retry settings when a
test intentionally exercises failure. Await observable state transitions
instead of sleeping for fixed delays.

```tsx
const queryClient = new QueryClient({
  defaultOptions: { queries: { retry: false } },
})

const wrapper = ({ children }: { children: React.ReactNode }) => (
  <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>
)
```

Clear ownership between tests prevents one test's cache from affecting another.

## Migration coverage

- React Query v2 to v3: dedicated `migrating-to-react-query-3` guide.
- React Query v3 to v4: package rename and behavioral/API changes.
- React Query v4 to v5: dedicated `migrating-to-v5` guide.
- Vue has a separate v5 migration.
- Svelte has a separate v5-to-v6 migration and must not be filed under React
  Query 5.102.8.

Migration pages describe source and target generations. Preserve them as
separate topics if a future batch indexes migration details verbatim.

## API map

The machine-readable index contains 256 generated API entries across supported
frameworks. Core repository references include `QueryClient`, `QueryCache`,
`MutationCache`, query observers, `focusManager`, `onlineManager`,
`notifyManager`, `timeoutManager`, `environmentManager`, and `streamedQuery`.

React-facing references include provider and hydration components, query and
mutation hooks, suspense hooks, prefetch hooks, option helpers, error-reset
boundaries, and result/option types.

## Gaps

- This batch maps API families but does not index 256 generated signatures.
- Framework-specific SSR mechanics remain outside the Query package's control.
- Experimental persistence/broadcast APIs require explicit stability labels.
- The docs corpus is labeled v5 even though Svelte Query is on v6 and Lit Query
  is on 0.2.x.

## Sources

- https://tanstack.com/query/latest/docs/framework/react/guides/advanced-ssr.md
- https://tanstack.com/query/latest/docs/framework/react/plugins/persistQueryClient.md
- https://tanstack.com/query/latest/docs/framework/react/guides/testing.md
- https://tanstack.com/query/latest/docs/framework/react/guides/migrating-to-v5.md
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/reference
