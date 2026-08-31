---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "React fields, validation, and submission"
source: "https://tanstack.com/form/latest/docs/framework/react/quick-start"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-form@1.33.5; moving stable v1 docs"
---

# React forms with TanStack Form

TanStack Form infers form value types from `defaultValues`. Fields expose their value, metadata, change handler, and blur handler.

## Installation

```sh
npm install @tanstack/react-form
```

Version 1.33.5 supports React 17, 18, and 19.

## Define a validated field

```tsx
import { useForm } from '@tanstack/react-form'

export function ProfileForm() {
  const form = useForm({
    defaultValues: { age: 0 },
    onSubmit: ({ value }) => console.log(value),
  })

  return (
    <form
      onSubmit={(event) => {
        event.preventDefault()
        void form.handleSubmit()
      }}
    >
      <form.Field
        name="age"
        validators={{
          onChange: ({ value }) => value >= 13 ? undefined : 'Must be 13 or older',
        }}
      >
        {(field) => (
          <>
            <input
              name={field.name}
              type="number"
              value={field.state.value}
              onBlur={field.handleBlur}
              onChange={(event) => field.handleChange(event.target.valueAsNumber)}
            />
            {!field.state.meta.isValid && <p>{field.state.meta.errors.join(', ')}</p>}
          </>
        )}
      </form.Field>
      <button type="submit">Save</button>
    </form>
  )
}
```

## Notes

- Prevent native form submission and call `form.handleSubmit()`.
- Validation may be field-specific or form-wide.
- For reusable application-wide field components, the docs recommend composing a form hook with `createFormHook`.
- A 2.x alpha exists, but the official `latest` docs currently present the stable v1 API.

## Sources

- https://tanstack.com/form/latest/docs/installation
- https://github.com/TanStack/form/blob/main/packages/react-form/CHANGELOG.md
