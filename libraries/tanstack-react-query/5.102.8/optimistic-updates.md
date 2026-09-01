---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "optimistic mutation updates and rollback"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/optimistic-updates.md"
retrieved_at: "2026-08-31"
source_ref: "release-2026-08-27-1607 / 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Optimistic mutation updates and rollback

TanStack Query supports two optimistic-update styles. A UI-only optimistic update renders pending mutation variables without changing cached query data. This is the lower-risk choice when only one screen needs the temporary item. Mutation state can expose pending variables and submission time, including from another component when a mutation key is shared.

A cache-level optimistic update changes query data in `onMutate`. Cancel relevant queries first so an in-flight refetch does not overwrite the optimistic value. Snapshot the previous data, write a new immutable value, and return rollback context. If the mutation fails, restore the snapshot or refetch. After settlement, invalidate the affected query so the server's canonical state replaces the estimate.

Optimistic logic must match server conflict and ordering rules. Temporary IDs need a strategy that cannot collide with real IDs. Concurrent mutations can settle in a different order than they were submitted, so one rollback must not erase another successful optimistic change. Mutation keys and submitted timestamps can help distinguish concurrent pending operations, but complex shared edits may be safer with server reconciliation instead of cache prediction.

Do not optimistically invent fields the server controls unless the UI clearly treats them as provisional. If a failed request cannot be refetched, retain enough rollback context to recover. Surface failure state rather than silently removing the user's action.

Always update cached arrays and objects immutably. Direct mutation can make the optimistic item appear inconsistently across observers. Keep list and detail caches synchronized or invalidate both after settlement.

## Sources

- https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/optimistic-updates.md
- https://github.com/TanStack/query/tree/2969edf32f7e0c48e2a108d84712d6e01edfde21/examples/react/nextjs-app-optimistic-updates


