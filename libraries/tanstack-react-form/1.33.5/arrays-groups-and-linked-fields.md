---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "arrays groups and linked fields"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/arrays.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Arrays, groups, and linked fields

Array fields expose mutation helpers for adding, removing, swapping, and moving items while keeping field metadata aligned. Declare the field with array mode and render nested item paths from the current array. Use stable application identifiers for React keys when items have them; array indexes are field-path positions and can change after a move.

Avoid mutating the array value in place. Use the field API so validation, touched state, and subscriptions observe the update. Nested item fields retain full deep-path typing when the form defaults describe the array element shape.

Form groups collect a related subset of fields behind a typed group API. They support reusable validation, listeners, metadata, and components without forcing the group to become a separate form. Field groups are useful for address blocks, credentials, repeated domain objects, and multi-step sections. When a group is reused at different paths, define the mapping deliberately and keep its error renderer able to handle unknown error types.

Linked fields handle dependencies such as password confirmation, country/postal-code rules, or a derived total. Validation can read the linked values and rerun when they change. Keep the dependency direction explicit. Two listeners that continually rewrite each other's values create a loop and obscure which field is authoritative.

For very large repeated sections, subscribe at the item or summary level instead of making the entire form rerender for one nested change. Array-level rendering should respond to structural changes; individual item fields should own their own value updates.

## Sources

- [Arrays guide](https://tanstack.com/form/latest/docs/framework/react/guides/arrays.md)
- [Form groups guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/form-groups.md)
- [Linked fields guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/linked-fields.md)
- [Array example](https://tanstack.com/form/latest/docs/framework/react/examples/array.md)

