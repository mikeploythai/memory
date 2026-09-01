---
library: "@tanstack/react-query"
version: "5.102.8"
topic: "mutations, invalidation, and optimistic updates"
source: "https://github.com/TanStack/query/blob/2969edf32f7e0c48e2a108d84712d6e01edfde21/docs/framework/react/guides/mutations.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-query@5.102.8; commit 2969edf32f7e0c48e2a108d84712d6e01edfde21"
---

# Mutations, invalidation, and optimistic updates

Mutations create, update, or delete remote data. They are not identified and
deduplicated like ordinary queries. Use mutation callbacks to coordinate cache
updates and related refetches.

## Invalidate after success

```tsx
import { useMutation, useQueryClient } from '@tanstack/react-query'

function AddTodo() {
  const queryClient = useQueryClient()
  const mutation = useMutation({
    mutationFn: (title: string) =>
      fetch('/api/todos', {
        method: 'POST',
        headers: { 'content-type': 'application/json' },
        body: JSON.stringify({ title }),
      }).then((response) => {
        if (!response.ok) throw new Error('Unable to add todo')
        return response.json()
      }),
    onSuccess: async () => {
      await queryClient.invalidateQueries({ queryKey: ['todos'] })
    },
  })

  return (
    <button onClick={() => mutation.mutate('Write tests')}>
      Add todo
    </button>
  )
}
```

Invalidation marks matching queries stale and refetches active matches according
to Query's rules. Use filters to target the intended key family.

## Update from a mutation response

If the server returns the canonical updated object, write that response into
the exact cache entry instead of immediately fetching it again.

```ts
onSuccess: (savedTodo) => {
  queryClient.setQueryData(['todo', savedTodo.id], savedTodo)
}
```

Treat cached values as immutable. Return a new object or collection rather than
mutating the previous cache value in place.

## Optimistic update with rollback

```ts
const mutation = useMutation({
  mutationFn: updateTodo,
  onMutate: async (nextTodo) => {
    await queryClient.cancelQueries({ queryKey: ['todo', nextTodo.id] })
    const previous = queryClient.getQueryData(['todo', nextTodo.id])
    queryClient.setQueryData(['todo', nextTodo.id], nextTodo)
    return { previous }
  },
  onError: (_error, nextTodo, context) => {
    queryClient.setQueryData(['todo', nextTodo.id], context?.previous)
  },
  onSettled: (_data, _error, nextTodo) => {
    return queryClient.invalidateQueries({ queryKey: ['todo', nextTodo.id] })
  },
})
```

Cancel the related query before taking the snapshot so an in-flight response
does not overwrite the optimistic value. Return rollback context from
`onMutate`, restore it on failure, and reconcile with the server afterward.

## Mutation state

Mutation results expose pending, error, success, and idle states. `mutate` is
callback-oriented; `mutateAsync` returns a promise. Handle promise rejection
when using `mutateAsync`.

Mutation scopes can serialize selected mutations. Offline mutation behavior
also depends on network mode and persisted mutation configuration; do not infer
offline replay from ordinary cache persistence alone.

## Failure modes

- Invalidating an overly broad prefix can refetch unrelated screens.
- Invalidating only a detail query can leave a list stale, and vice versa.
- In-place cache mutation can defeat observer notifications and structural
  sharing.
- An optimistic update without rollback leaves fabricated data after failure.
- Fire-and-forget `mutateAsync` calls can create unhandled rejections.
- Client success does not replace server-side authorization or validation.

## Sources

- https://tanstack.com/query/latest/docs/framework/react/guides/query-invalidation.md
- https://tanstack.com/query/latest/docs/framework/react/guides/invalidations-from-mutations.md
- https://tanstack.com/query/latest/docs/framework/react/guides/updates-from-mutation-responses.md
- https://tanstack.com/query/latest/docs/framework/react/guides/optimistic-updates.md
- https://tanstack.com/query/latest/docs/framework/react/guides/network-mode.md
