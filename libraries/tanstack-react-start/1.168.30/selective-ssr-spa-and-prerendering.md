---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "selective SSR, SPA mode, and static prerendering"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/selective-ssr.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Selective SSR, SPA mode, and static prerendering

Start can choose rendering behavior per route. With SSR enabled, the initial server request runs the route lifecycle, renders HTML, and sends hydration data. Selective SSR changes how much of that work happens on the server for a route. The route's `ssr` setting can be static or derived according to the guide, while a Start-level default establishes application behavior.

Disabling server rendering is not the same as making code server-only or client-only. Route loaders remain part of the application execution model, and server functions still run on the server. A client-rendered route must provide an appropriate pending shell and cannot rely on server HTML for search indexing or no-JavaScript behavior.

SPA mode serves an application shell and performs route rendering in the browser. It suits deployments that do not need per-request HTML, but direct URL requests still require the host to route application paths to the shell. Server routes and server functions still need a server-capable deployment if the application uses them.

Static prerendering generates HTML for known paths at build time. Every required dynamic path must be enumerated or discovered through the supported configuration. Build-time code cannot depend on a live request, user cookie, or per-request identity. Rebuild or use the documented regeneration strategy when content changes.

Choose modes by route requirements, not as a blanket performance label. Public stable pages often benefit from prerendering; personalized pages require request or client data; highly interactive private tools may accept an SPA shell. Test direct loading, hydration, redirects, and error behavior in every selected mode. A route that works during client navigation can still fail when loaded directly under a different server policy.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/selective-ssr.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/spa-mode.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/static-prerendering.md


