---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "server rendering and deferred route data"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/ssr.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Server rendering and deferred route data

Server rendering requires a router instance scoped to the incoming request. The server loads the requested location, renders the matched route tree, serializes the router state, and sends it with the document. The browser creates its own router, hydrates the serialized state, and continues navigation. Never reuse a server router or request-bound context across users.

Loaders used during SSR must return serializable values. Browser-only globals cannot run during server rendering, and server credentials must not be included in loader results. A loader can call a server-side data layer, but the value crossing into hydration becomes client-visible. Use request context for cookies, headers, and user identity, and enforce authorization on the server data boundary.

Deferred data allows a route to render available content while a promise resolves. The route can expose deferred work and render it through the router's awaiting APIs and suspense boundaries. Put error handling near the deferred consumer so a late failure does not necessarily replace the whole document. Do not defer values required to decide access, redirects, or the basic route layout; those decisions must complete before unsafe content renders.

Hydration requires the server and client's initial tree and data assumptions to agree. Time-dependent, random, locale-dependent, and browser-only rendering can cause mismatches. Keep request-scoped data deterministic and move client-only behavior behind an appropriate client boundary.

For a full-stack application, TanStack Start supplies the supported SSR integration around Router. The Router guide explains primitives, but hand-rolled SSR must also own document assembly, streaming, serialization, and error handling.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/ssr.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/deferred-data-loading.md


