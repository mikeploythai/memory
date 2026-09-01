---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "React validation submission and composition"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/validation.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-form@1.33.5 (b865ef335a69aa08a2f160895258f13e03773467)"
---

# React validation, submission, and composition

The React adapter can validate at field or form scope, synchronously or
asynchronously, and at different interaction events. Choose an event that
matches the cost and user experience of the rule.

## Field validation

```tsx
<form.Field
  name="age"
  validators={{
    onChange: ({ value }) =>
      value < 13 ? 'You must be at least 13' : undefined,
  }}
>
  {(field) => (
    <>
      <input
        type="number"
        value={field.state.value}
        onBlur={field.handleBlur}
        onChange={(event) => field.handleChange(event.target.valueAsNumber)}
        aria-invalid={field.state.meta.isTouched && !field.state.meta.isValid}
      />
      {field.state.meta.errors.map((error) => (
        <p key={String(error)}>{String(error)}</p>
      ))}
    </>
  )}
</form.Field>
```

Validator return types flow into the error map and error array. Errors need not
be strings, but UI code must render the chosen error shape intentionally.

## Validation events

| Event | Typical use |
|---|---|
| `onChange` | inexpensive feedback while typing |
| `onBlur` | checks that should wait until focus leaves |
| `onChangeAsync` | debounced server or network checks |
| `onSubmit` | final cross-field or business invariant |
| `onDynamic` | rules selected by submission or form state |

Dynamic validation is opt-in. The official guide requires `revalidateLogic()`
before `onDynamic` is invoked:

```ts
const form = useForm({
  defaultValues: { username: '' },
  validationLogic: revalidateLogic(),
  validators: {
    onDynamic: ({ value }) =>
      value.username ? undefined : { username: 'Username is required' },
  },
})
```

Async dynamic validation can set a debounce interval. Account for stale
responses and cancellation when the validator crosses the network.

## Schema validation

The stable docs support Standard Schema-compatible validators such as Zod,
Valibot, ArkType, and Effect/Schema. Schema validation reports issues; it does
not provide transformed submission values. Apply transformations deliberately
in submission or application logic.

## Submission

Native form submission should call `preventDefault()` and then
`form.handleSubmit()`. The Form API validates before invoking `onSubmit` and
exposes `isSubmitting` for pending UI.

`canSubmit` has interaction-sensitive semantics. Do not treat it as the only
proof that a pristine form is complete. If the product disallows pristine
submission, combine it with the documented pristine state.

Disabled buttons are not always the best accessible error path. Consider
`aria-disabled`, visible validation feedback, and focus movement to the first
invalid field as product-level behavior.

## Composition

The React adapter supports reusable form contexts, pre-bound field components,
`createFormHook`, `withForm`, form groups, and linked fields. Composition should
preserve field-name and value inference rather than hiding the form behind an
untyped component API.

Use granular subscriptions in reusable controls. Reading broad form state in a
top-level component can rerender more of a large form than necessary.

## Failure modes

- Omitting `revalidateLogic()` means `onDynamic` does not run.
- Mutating values outside field APIs bypasses metadata and validation.
- Rendering arbitrary object errors as React children can fail at runtime.
- An async validator without debouncing may issue a request per keystroke.
- Schema parsing does not automatically replace the submitted value with a
  transformed value.

## Sources

- https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/dynamic-validation.md
- https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/submission-handling.md
- https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/form-composition.md
- https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/form-groups.md
- https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/linked-fields.md

## Gaps

This page retains selected validation and composition patterns, not every React
feature contract. Arrays, async initial values, UI-library integrations, and
application-specific server errors, focus policy, localization, and accessible
summary patterns remain outside its scope.
