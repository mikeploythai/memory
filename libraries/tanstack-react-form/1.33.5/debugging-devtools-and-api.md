---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "debugging devtools and API map"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/debugging.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Debugging, devtools, and API routing

An uncontrolled-to-controlled warning usually means a field's default value was `undefined` and later became defined. Supply a complete default shape or intentionally keep that control uncontrolled for its full lifetime. Do not silence the warning with a cast; it describes a real ownership change in React.

When a field value is inferred as `unknown`, inspect the default-value type, field path, reusable helper generics, and any context boundary. Deeply composed generic forms can also produce TypeScript's “type instantiation is excessively deep” error. The code may run, but the type design is too complex for the compiler. Shorten extension chains, split types, or use a smaller typed boundary.

TanStack Form Devtools can inspect form and field state, validation metadata, and submission behavior. Install both the shared React Devtools host and the Form plugin. Keep devtools out of production bundles unless the product intentionally exposes them.

The core API index covers `FormApi`, `FieldApi`, group APIs, validators, listener types, deep-key/value utilities, state, and update functions. The React reference covers `useForm`, `useField`, field components, selectors, subscriptions, contexts, composition helpers, and transforms. Use generated symbol pages for exact signatures and these topic guides for lifecycle and ownership decisions.

Debug by checking four layers in order: value/default shape, field-name inference, validation event/error map, and React subscription. A correct value in the form store with stale UI usually points to subscription or control wiring; a missing value usually points to field naming or defaults.

## Sources

- [Debugging guide](https://tanstack.com/form/latest/docs/framework/react/guides/debugging.md)
- [Devtools guide](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/devtools.md)
- [Core API](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/reference/index.md)
- [React API](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/reference/index.md)


