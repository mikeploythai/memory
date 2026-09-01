---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "search parameter validation and serialization"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/search-params.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Search parameter validation and serialization

TanStack Router treats the URL search string as typed application state. A route's `validateSearch` function parses untrusted raw search values and returns the typed shape available to loaders, navigation, and components. Child routes inherit parent search values, so validation should be scoped to the route that owns each field. Validation libraries can be used through adapters, but defaults and fallback behavior must still be explicit.

Read search state through a route-scoped API when possible. A route's `useSearch` narrows the result to its validated schema. Looser access is available for shared components, but strict route identity gives TypeScript the strongest guarantees. When navigating, the `search` option can replace or transform the current search state. Preserve existing values deliberately rather than relying on string concatenation.

The default serializer supports JSON-compatible values, including nested objects and arrays, while keeping top-level search keys URL-addressable. Custom serialization is available through router-level `parseSearch` and `stringifySearch`. The parser and serializer must be a reversible pair. If they disagree, links may not round-trip, cache keys can diverge from visible URLs, and back/forward navigation can restore a different state than the one originally produced.

Search input is external input. Do not assume a type merely because a link inside the application generated it. Validate malformed, missing, repeated, and legacy values. Apply defaults in validation so loaders and components see one normalized representation. Avoid putting large or sensitive values in the URL; search state is visible, shareable, and retained in browser history.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/search-params.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/custom-search-param-serialization.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to/validate-search-params.md


