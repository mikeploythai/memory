---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "UI focus and native patterns"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/ui-libraries.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# UI libraries, focus, and React Native

TanStack Form supplies state and handlers, not input markup. A component-library adapter must map the control's actual value and blur semantics to `field.handleChange` and `field.handleBlur`. Some libraries pass a value directly; DOM inputs pass an event. Keep that conversion in a typed shared field component rather than repeating casts at every use.

Render validation feedback from field metadata and connect it to the control with the platform's accessibility mechanism. In the DOM, labels, IDs, `aria-invalid`, and described-by relationships remain application responsibilities. Do not show all errors solely by joining unknown values into a string; schema and custom validators can produce structured errors.

After a failed submission, focusing the first invalid input improves recovery. The focus-management guide demonstrates finding the first field error and focusing the registered element. Preserve document order rather than object iteration assumptions when order matters. For controls that cannot be focused directly, expose a ref to the interactive element.

React Native uses different control events and ref/focus APIs. There is no browser form element, native submit event, or DOM `name` attribute. Bind native text/value changes to the field API and implement focus using native refs. Shared domain validation can remain platform-neutral, while field components should be platform-specific.

Headless integration does not automatically make a component library accessible. Verify keyboard operation, error announcement, required-state communication, and focus behavior in the rendered control. Use the official UI-library example as a wiring reference, then confirm the selected library's current component contract.

## Sources

- [UI libraries guide](https://tanstack.com/form/latest/docs/framework/react/guides/ui-libraries.md)
- [Focus management](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/focus-management.md)
- [React Native guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/react-native.md)
- [UI-library example](https://tanstack.com/form/latest/docs/framework/react/examples/ui-libraries.md)


