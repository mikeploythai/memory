---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "concepts TypeScript and quick start"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/quick-start.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Concepts, TypeScript, and quick start

TanStack Form is a headless form-state library. `useForm` creates the form instance; `form.Field` binds a typed path to a field instance; `form.Subscribe` renders from selected form state. Application code owns labels, controls, error markup, styling, accessibility, and submission transport.

Define complete `defaultValues` so TypeScript can infer the form shape and React controls remain controlled for their full lifetime. Nested field names are checked through deep-key types. A field exposes its current value and metadata plus handlers such as `handleChange` and `handleBlur`; wire those handlers to the actual control rather than duplicating field state in local React state.

`formOptions` creates reusable typed configuration. Spread those options into `useForm` and add instance-specific submission behavior. Subscribe only to the state needed by a component, such as `canSubmit` and `isSubmitting`, rather than reading all form state high in the component tree.

The basic submit pattern prevents the browser's default navigation, then calls `form.handleSubmit()`. The handler receives the typed form value. Reset through `form.reset()` and prevent the browser's native reset behavior when it would produce a different result, especially for select controls.

Type inference is strongest when defaults, schemas, field paths, and reusable form helpers share the same declared shape. If a field becomes `unknown`, first verify default values and field-name inference before adding casts. Casts hide the mismatch that the deep-key types are designed to find.

## Sources

- [React quick start](https://tanstack.com/form/latest/docs/framework/react/quick-start.md)
- [Basic concepts](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/basic-concepts.md)
- [TypeScript guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/typescript.md)


