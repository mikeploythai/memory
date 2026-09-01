---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "custom server and client entry points"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-entry-point.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Custom server and client entry points

Start supplies default server and client entry behavior. Add custom entry points only when the application needs request wrapping, provider setup, instrumentation, response transformation, custom hydration, or hosting integration that the defaults do not cover.

The server entry receives an incoming request and delegates to Start's request handler. Preserve that delegation so Router matching, server routes, server functions, SSR, streaming, headers, and error handling continue to work. Request-scoped dependencies belong in the request path. Do not create a process-global router, Query client, session, or user context that can cross requests.

Response customization must preserve streaming semantics. Buffering or reconstructing the response can defeat streaming, lose headers, or mishandle status codes. Add headers or instrumentation through documented transforms or middleware when possible. Ensure thrown redirects and not-found results still reach Start's handler.

The client entry hydrates the server-rendered application. It should create stable browser-scoped providers and invoke Start's client integration once. Recreating the router or Query client during render discards hydrated state and can issue duplicate requests. Client-only monitoring belongs after the browser environment exists.

Server and client provider trees must produce compatible initial markup. If a provider reads time, storage, media state, or random values during initialization, supply a deterministic server value or defer that behavior until after hydration.

Keep entry files small. Application data loading, authentication rules, and domain logic belong in routes, middleware, and server modules. A large custom entry point makes upgrades harder because it duplicates framework behavior that Start otherwise owns.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-entry-point.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/client-entry-point.md


