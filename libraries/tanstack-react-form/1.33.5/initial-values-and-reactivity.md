---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "initial values and reactivity"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/async-initial-values.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Initial values and reactivity

Forms often begin with data loaded asynchronously. Keep a complete shape available while loading so React inputs do not switch from uncontrolled `undefined` values to controlled values later. Once remote data is available, initialize or reset the form deliberately. Do not recreate the whole form instance on every request-state render.

TanStack Query can own fetching and caching while TanStack Form owns editable state. Treat the query result as an initialization source, not a continuously authoritative value that overwrites user edits on each refetch. Decide whether a successful refetch should leave dirty fields untouched, reset the form, or prompt the user.

Use `useSelector` to subscribe to selected form state outside render-prop components. `useStore` remains exported through the store adapter but is deprecated; migrate to `useSelector` with the same selector arguments. A custom comparison function is passed through the options form documented by the adapter.

Inside form markup, `form.Subscribe` is often clearer. Select only the values required by that subtree, such as submit eligibility, pending state, or a derived total. Broad subscriptions cause unrelated controls or summaries to rerender for every field change. Direct reads from the form API do not automatically establish a React subscription.

Keep server state and form state conceptually separate. Query invalidation after submission may fetch canonical data, but resetting immediately can erase optimistic or unsaved edits. Establish the transition explicitly: submit, await the authoritative result, update or invalidate the query, and then reset only when the product behavior calls for it.

## Sources

- [Async initial values](https://tanstack.com/form/latest/docs/framework/react/guides/async-initial-values.md)
- [Reactivity guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/reactivity.md)
- [TanStack Query integration example](https://tanstack.com/form/latest/docs/framework/react/examples/query-integration.md)


