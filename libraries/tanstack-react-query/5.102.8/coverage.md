---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "documentation coverage map"
source: "https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Documentation coverage map

This is the bounded first depth batch for React Query 5.102.8. `indexed` means a retrieval page exists here; `deferred` means exact-tag material exists for a later batch; `not present` means there is no dedicated exact-tag page.

## Indexed in this batch

| Status | Memory page | Exact-tag source topics |
|---|---|---|
| indexed | `important-defaults-and-cache-lifecycle.md` | important defaults, caching |
| indexed | `queries-and-invalidation.md` | queries, keys, functions, invalidation |
| indexed | `parallel-dependent-queries-and-waterfalls.md` | parallel, dependent, waterfalls |
| indexed | `pagination-and-placeholder-data.md` | pagination, placeholder data |
| indexed | `infinite-queries.md` | infinite queries and exact examples |
| indexed | `mutations-invalidation-and-cache-updates.md` | mutations, mutation invalidation, response updates |
| indexed | `optimistic-updates.md` | optimistic guide and example |
| indexed | `cancellation-retries-and-network-mode.md` | cancellation, retry, network mode |
| indexed | `prefetching-and-router-integration.md` | prefetching and Router integration |
| indexed | `ssr-hydration-and-advanced-ssr.md` | SSR, advanced SSR, hydration |
| indexed | `render-optimization-and-suspense.md` | rendering and suspense |
| indexed | `testing.md` | testing guide |

## Deferred exact-tag corpus

- Getting started: `overview.md`, `installation.md`, `quick-start.md`, `devtools.md`, `comparison.md`, `typescript.md`, `graphql.md`, `react-native.md`.
- Remaining React guides: `background-fetching-indicators.md`, `window-focus-refetching.md`, `polling.md`, `disabling-queries.md`, `initial-query-data.md`, `scroll-restoration.md`, `filters.md`, `default-query-function.md`, `does-this-replace-client-state.md`, and migrations to React Query 3, 4, and 5. The disabled-query tradeoffs remain explicitly deferred rather than folded into a generic query page.
- Persistence/plugins: `broadcastQueryClient.md`, `createAsyncStoragePersister.md`, `createPersister.md`, `createSyncStoragePersister.md`, `persistQueryClient.md`.
- React reference: hydration, query/infinite/mutation option helpers, provider and error-reset boundaries, `useQuery`, `useQueries`, suspense hooks, infinite-query hooks, mutation hooks, prefetch hooks, query-client hooks, and fetching/mutating status hooks under `docs/framework/react/reference/`.
- Core reference: `QueryClient`, `QueryCache`, `MutationCache`, query/infinite/queries observers, focus/online/notify/timeout/environment managers, and `streamedQuery` under `docs/reference/`.
- Exact-tag React examples: simple/basic, GraphQL, polling, optimistic updates, pagination, infinite scrolling, max pages, suspense, default function, prefetching, Next.js pages/prefetch/streaming, React Native, React Router, offline, Algolia, Shadow DOM, embedded Devtools, streaming chat, and batching. Example source is deferred unless cited by an indexed topic.
- Other framework docs are outside this React package batch and are not implied by shared core concepts.

## Not present as dedicated exact-tag pages

- No single anti-patterns page; failure modes must retain links to their specific guide.
- No normalized-cache entity model; Query organizes server state by query keys.
- No guarantee that hosted `latest` matches 5.102.8 despite the v5 label; immutable commit content is authoritative for this directory.

Stopping point: twelve semantic pages plus this map. The API, persistence, migration, remaining guides, and complete examples require later bounded batches.

## Sources

- https://tanstack.com/query/latest/llms.txt
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/reference
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/examples/react

