---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "route preloading and code splitting"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/preloading.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Route preloading and code splitting

Preloading starts route code and data before navigation commits. Supported link strategies include user intent, viewport visibility, and render-time preloading. Intent is a useful application default because focus, hover, and touch indicate likely navigation without fetching every rendered destination. A configurable delay reduces work caused by brief pointer movement.

Preloaded loader results have separate freshness and retention controls. `preloadStaleTime` decides how long successful preload data is fresh; `preloadGcTime` controls how long unused data can remain. The speculative match lane is not promoted wholesale into router state. A later navigation runs its own `beforeLoad` chain, though it can reuse settled loader data or join compatible in-flight loader work. Redirects, errors, and context from a completed preload should not be treated as a substitute for navigation-time authorization.

When TanStack Query or another external cache owns freshness, set Router preload freshness so the external cache makes the decision. Otherwise both layers may suppress or repeat work independently. A route with loader preloading disabled can still run `beforeLoad` in the speculative lane, so authorization logic must tolerate preloads and should use the supplied preload indicator when behavior differs.

Code splitting separates route-critical configuration from lazy components and other noncritical options. Automatic code splitting uses the Router bundler plugin and file conventions; manual lazy routes provide explicit control. Keep loader dependencies and route identity in the critical portion. Splitting them incorrectly can delay data discovery or weaken generated types. Generated split artifacts are build output and should not be manually edited.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/preloading.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/code-splitting.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/automatic-code-splitting.md


