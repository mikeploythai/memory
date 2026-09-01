---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "React quick start and basic concepts"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/quick-start.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-form@1.33.5 (b865ef335a69aa08a2f160895258f13e03773467)"
---

# React quick start and basic concepts

This page records the React adapter's basic form lifecycle. Other adapters use
the same broad form and field ideas through different framework bindings.

## Create a form

`defaultValues` establish the initial value shape and drive TypeScript
inference. The submit callback receives the complete typed value.

```tsx
import { useForm } from '@tanstack/react-form'

export function ProfileForm() {
  const form = useForm({
    defaultValues: {
      fullName: '',
      age: 0,
    },
    onSubmit: async ({ value }) => {
      console.log(value)
    },
  })

  return (
    <form
      onSubmit={(event) => {
        event.preventDefault()
        void form.handleSubmit()
      }}
    >
      <form.Field name="fullName">
        {(field) => (
          <label>
            Full name
            <input
              name={field.name}
              value={field.state.value}
              onBlur={field.handleBlur}
              onChange={(event) => field.handleChange(event.target.value)}
            />
          </label>
        )}
      </form.Field>

      <form.Subscribe selector={(state) => [state.canSubmit, state.isSubmitting]}>
        {([canSubmit, isSubmitting]) => (
          <button type="submit" disabled={!canSubmit || isSubmitting}>
            {isSubmitting ? 'Saving...' : 'Save'}
          </button>
        )}
      </form.Subscribe>
    </form>
  )
}
```

## Adapter concepts retained here

- The form API owns values, validation, submission state, and field metadata.
- A field subscribes to its own value and metadata rather than rerendering the
  complete form.
- `handleBlur` updates blur metadata and can trigger blur validation.
- `handleChange` updates the field through the Form API.
- `form.Subscribe` rerenders for its selected state.
- `handleSubmit()` runs submission validation before calling `onSubmit`.

## Field names and values

Nested object and array paths are typed from `defaultValues`. Keep the default
shape complete enough for the fields used by the form. Avoid changing a field
between incompatible value types after inference.

Number inputs require deliberate conversion. For a numeric field, React can
read `valueAsNumber`:

```tsx
onChange={(event) => field.handleChange(event.target.valueAsNumber)}
```

## Verification

The official quick start does not define a project-level command. In an
existing React app, verify that:

1. TypeScript accepts field names and value handlers.
2. Editing the input updates the field value.
3. Native submission does not reload the page.
4. `onSubmit` receives the complete typed object.
5. The submitting state prevents duplicate submission.

Use the host application's actual development, test, and build scripts. Their
names are outside TanStack Form's documentation contract.

## Other quick starts

- https://tanstack.com/form/latest/docs/framework/preact/quick-start.md
- https://tanstack.com/form/latest/docs/framework/vue/quick-start.md
- https://tanstack.com/form/latest/docs/framework/angular/quick-start.md
- https://tanstack.com/form/latest/docs/framework/solid/quick-start.md
- https://tanstack.com/form/latest/docs/framework/lit/quick-start.md
- https://tanstack.com/form/latest/docs/framework/svelte/quick-start.md

## Sources

- https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/basic-concepts.md
- https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/typescript.md

## Gaps

The retained component covers the basic lifecycle only. Arrays, async initial
values, reusable UI integrations, SSR, React Native, server-error handling, and
the complete generated adapter API remain outside this page.
