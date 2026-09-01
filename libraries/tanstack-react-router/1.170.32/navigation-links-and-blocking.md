---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "navigation, links, and navigation blocking"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/navigation.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Navigation, links, and navigation blocking

Navigation APIs share the same typed destination model: `to`, `from`, `params`, `search`, hash, state, and replacement behavior. `Link` is the normal declarative choice; `useNavigate` and `router.navigate` cover imperative flows. Supplying `from` anchors relative navigation and lets TypeScript infer the valid destination, params, and search schema. If `from` is omitted, the router assumes the root and can only offer reliable absolute-path completion.

Relative paths resolve from a route origin, not from an arbitrary component location. Use route IDs or full paths consistently when a component is reused. Params and search can be values or updater functions. Prefer typed options over building URLs manually so escaping, serialization, and route registration stay aligned.

`Link` also controls active-state props and preloading. Reusable link configurations can be built with `linkOptions`; custom link components should preserve the router's generated props and event behavior rather than implementing navigation with a raw click handler.

Navigation blocking is intended for cases such as unsaved user input. A blocker can inspect the current and next locations and decide whether to stop a transition. Blocking browser unloads is a separate concern from in-app navigation and may require the browser's unload confirmation behavior. Do not block every transition as a substitute for persisting state: blockers interrupt history navigation and can create confusing loops if the confirmation flow itself navigates.

Use `replace` for redirects or state normalization that should not create another history entry. Use push navigation for user-visible movement where Back should return to the prior location.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/navigation.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/link-options.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/navigation-blocking.md


