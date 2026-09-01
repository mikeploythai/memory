---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "submission and schema transforms"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/submission-handling.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Submission and schema transforms

Call `form.handleSubmit()` from the application's submit event after preventing unwanted browser navigation. The form coordinates validation, submission state, and the configured `onSubmit` callback. Use selected state such as `canSubmit` and `isSubmitting` to present feedback and prevent duplicate user actions, but keep validation in the submission path because a disabled button is not a security or correctness boundary.

Submission metadata can carry data that is not part of the form value, such as which action button was used. Keep that metadata separate from editable domain fields so validation and reset behavior remain predictable.

Standard Schema validators validate the input shape, but TanStack Form does not automatically replace the submitted value with the schema's transformed output. If a schema coerces, trims, normalizes, or otherwise transforms values, parse the value in `onSubmit` and use the parsed result. Type defaults as the schema input and treat the parsed value as the output.

Server errors need an explicit mapping. Preserve form-wide failures separately from field errors and merge them through the documented form/error APIs rather than maintaining an unrelated error store. Clear or replace server errors when their underlying values change according to the intended product behavior.

After a successful request, decide whether to reset to defaults, reset to the returned canonical record, leave dirty state visible, or navigate. Do not reset optimistically before the server succeeds unless losing the current edits is acceptable. A submission handler should also surface unexpected transport failures without presenting them as field-validation failures.

## Sources

- [Submission handling](https://tanstack.com/form/latest/docs/framework/react/guides/submission-handling.md)
- [Validation guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/validation.md)
- [Standard Schema example](https://tanstack.com/form/latest/docs/framework/react/examples/standard-schema.md)


