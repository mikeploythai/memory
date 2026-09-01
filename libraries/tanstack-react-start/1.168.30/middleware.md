---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "request and server-function middleware"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/middleware.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Request and server-function middleware

Middleware wraps server-function and request processing with reusable behavior. Common uses include authentication, request context, logging, timing, headers, and permission checks. A middleware can inspect the request-side context, add typed context for downstream middleware and handlers, and process the result after the next stage returns.

Order is observable. Earlier middleware wraps later middleware, so setup runs toward the handler and response processing unwinds in reverse. Authentication must run before middleware or handlers that consume the authenticated user. Error reporting should wrap the work it needs to observe. Document ordering when composing a shared stack; the same middlewares in another order can produce different authorization and headers.

Call the continuation exactly as the API requires. Forgetting to continue stops downstream execution, while calling it twice can duplicate a mutation. Return the downstream result unless the middleware intentionally replaces it. When short-circuiting for authentication or validation, use the documented error or redirect control flow.

Middleware context is request-scoped. Do not store a user or request object in a process-global variable. Derive identity from cookies or headers on every request and pass only the required typed values forward. Client-provided identifiers are input, not trusted identity.

Keep middleware cross-cutting. Business operations belong in the server function or route handler, where their input and permissions are explicit. Avoid hidden database writes in logging or auth middleware, especially when handlers can retry.

Separate client middleware behavior from server enforcement. Client hooks may add metadata or improve UX, but all security decisions must be repeated or centralized on the server path that owns the operation.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/middleware.md


