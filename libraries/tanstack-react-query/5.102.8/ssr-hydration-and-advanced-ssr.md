---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "server rendering, hydration, and advanced SSR"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/ssr.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Server rendering, hydration, and advanced SSR

Create a fresh `QueryClient` for each server request. Prefetch the queries needed for the route, dehydrate the client, serialize the dehydrated state safely, and hydrate it inside the client-side provider. Sharing a server client across requests can expose one user's cached data to another and lets cache growth span requests.

Server-prefetched queries should normally have a positive `staleTime`. Because query data is stale by default, a zero stale time can cause an immediate client refetch after hydration. Freshness is measured from when the server fetched the query, not from when the browser received the HTML, so long response or cache delays matter.

Only successful queries are dehydrated by default. If pending queries or errors are included through custom dehydration rules, ensure their values and errors can be serialized and that the client has matching behavior. Redact sensitive error details and never dehydrate server-only credentials.

Advanced server rendering can combine streaming and suspense. Prefetch queries for content that must be ready at a boundary, or allow supported pending queries to cross hydration when streaming. Server Components can prefetch and pass dehydrated state, but ownership matters: data rendered only on the server is not automatically kept in sync with a client query after revalidation.

The server and client must use identical query keys and compatible query functions. A key mismatch discards the value for hydration purposes and triggers another request. Avoid creating a new browser Query client on every render; initialize it in a stable client scope that survives suspense.

Treat dehydration as a public client payload. Inspect what enters it, especially user-specific data, errors, and long-lived caches.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/ssr.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/advanced-ssr.md
- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/reference/hydration.md


