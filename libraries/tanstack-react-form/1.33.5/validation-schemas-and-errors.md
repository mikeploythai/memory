---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "validation schemas and errors"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/validation.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Validation, schemas, and errors

Validation can run at field or form level on events such as mount, change, blur, and submit. A functional validator returns an error value or `undefined`. Field errors appear in field metadata; form errors appear on form state. Choose the event based on feedback cost and timing: inexpensive shape checks can run on change, while slower or more disruptive checks often belong on blur or submit.

Form validators can return both a form-level error and field errors. A field-specific validator for the same event may overwrite the field error supplied by the form validator. Preserve that precedence when troubleshooting a missing cross-field error. Use the event-specific `errorMap` when the UI needs to distinguish sources instead of flattening every error into one message.

TanStack Form accepts Standard Schema implementations, including current versions of Zod, Valibot, ArkType, and Effect Schema. Older schema-library versions may not expose the Standard Schema interface. Form-level schema errors propagate to fields. Their error-map shape differs from a simple string validator: Standard Schema issues are grouped by field and should be rendered accordingly.

Async validators use the dedicated async event handlers and can be debounced. Do not put every validation behind a network request. Keep local invariants synchronous, debounce remote availability checks, expose pending state, and always revalidate authoritative business rules on the server.

Prevent invalid submission through form validity and submit-state APIs rather than relying only on a disabled button. Programmatic submission still needs the same validation path.

## Sources

- [Validation guide](https://tanstack.com/form/latest/docs/framework/react/guides/validation.md)
- [Custom errors guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/custom-errors.md)
- [Field errors from form validators example](https://tanstack.com/form/latest/docs/framework/react/examples/field-errors-from-form-validators.md)


