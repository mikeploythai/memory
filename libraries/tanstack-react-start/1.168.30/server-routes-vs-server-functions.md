---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "server routes compared with server functions"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-routes.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Server routes compared with server functions

Server routes expose HTTP endpoints through the Start route-file system. A route defines method handlers and receives a web `Request`-oriented context. Use a server route when the HTTP contract matters directly: webhooks, public APIs, file or stream responses, third-party callbacks, custom status codes, or endpoints consumed outside the Start application.

Server functions expose application RPC. Client and server code call a typed function while Start handles transport. Use them for application operations invoked from loaders or components when a custom public HTTP representation is unnecessary. They still cross an untrusted network boundary and require runtime input validation, authentication, and authorization.

Server route filenames follow Router's file-based conventions, including dynamic parameters, escaped characters, pathless layouts, and breakout behavior. Only one handler file can own a resolved route path. Different filenames that normalize to the same URL create a conflict rather than multiple layers of handlers. Use middleware or method handlers inside the owning route instead.

Choose one boundary for an operation. A client should not call a server route and a server function that both implement the same mutation unless one intentionally delegates to shared domain logic. Duplicate public entry points drift in validation, permissions, and response behavior.

Server routes should return `Response` objects with deliberate headers and status codes. Parse body, params, and query values as untrusted input. Server functions return serializable application values and integrate more directly with Start's RPC and Router control flow.

Both run on the server, but neither makes the caller trustworthy. Keep core domain logic in server-only modules that both boundary types can call after each has authenticated and validated its own request.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-routes.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-functions.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/router/routing/file-based-routing.md


