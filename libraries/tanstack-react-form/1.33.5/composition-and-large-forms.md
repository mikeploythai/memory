---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "composition and large forms"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/form-composition.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Composition and large forms

`createFormHook` builds an application-specific form hook with pre-bound field and form components. This is the main pattern for sharing labels, controls, errors, and submit UI while preserving field-name and value inference. The field context consumed by a shared component must be the same context exported by the custom form setup.

`withForm` packages a typed form section or workflow around known defaults and props. Use it to split large forms into smaller components without passing a loosely typed generic form everywhere. Field groups provide a similar boundary for reusable subsets that may appear under different paths.

Prefer explicit typed props and `withForm` before reaching for a general form context. Context is a last resort when component placement makes normal composition impractical. A context value cannot prove that the consuming component's expected form shape matches the provider, so misalignment can become a runtime error rather than a compile-time error.

Keep extension chains shallow. Extending an application form repeatedly is supported, but long chains increase TypeScript work and can lead to “type instantiation is excessively deep” errors. Define a small shared base and compose product-specific behavior near the form that uses it.

Large-form performance depends on subscription boundaries. A context update or broad form-state read can rerender a large subtree. Let fields subscribe to their own state, use selected `Subscribe` boundaries for summaries and buttons, and avoid threading the complete reactive state through every component. Multi-step forms should preserve one intentional form state model while controlling which step is mounted and validated.

## Sources

- [Form composition guide](https://tanstack.com/form/latest/docs/framework/react/guides/form-composition.md)
- [Large-form example](https://tanstack.com/form/latest/docs/framework/react/examples/large-form.md)
- [Multi-step wizard](https://tanstack.com/form/latest/docs/framework/react/examples/multi-step-wizard.md)


