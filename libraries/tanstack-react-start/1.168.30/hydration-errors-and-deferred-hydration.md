---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "hydration errors and deferred hydration"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/hydration-errors.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Hydration errors and deferred hydration

Hydration requires the browser's first render to match the server HTML. Differences can come from browser-only APIs, time and randomness, locale or timezone formatting, invalid HTML nesting, extensions that alter markup, and data that changed between server rendering and client hydration. Fix the differing input rather than suppressing the warning globally.

Render deterministic shared output on both sides. Move access to `window`, storage, media queries, and layout measurements behind a client boundary or effect. If a value cannot be known on the server, render a stable fallback and replace it after hydration. Pass request-derived locale and timezone explicitly when formatted output must agree.

Invalid HTML can be reparsed by the browser into a tree different from React's server tree. Validate nesting before blaming data. Also inspect serialized loader or query state: a client refetch or a different cache key can change content during the hydration window.

Deferred hydration delays hydrating a subtree until a trigger or condition. It can reduce initial client work for noncritical UI, but the deferred HTML remains visible before it becomes interactive. The fallback must be safe and usable enough for that interval, and event-dependent controls should not appear fully active when they are not.

Do not use deferred hydration to hide a persistent server/client mismatch. The subtree still needs compatible initial markup when hydration eventually begins. Avoid deferring essential navigation, authentication controls, or content whose stale server HTML would mislead the user.

Debug from the smallest mismatched subtree. Compare the exact server markup and first client inputs, then reintroduce environment-specific behavior after a stable boundary is established.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/hydration-errors.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/deferred-hydration.md


