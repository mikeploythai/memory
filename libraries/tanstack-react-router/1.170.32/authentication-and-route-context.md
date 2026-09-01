---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "authenticated routes and router context"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/authenticated-routes.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Authenticated routes and router context

Router context is the dependency-injection channel shared by a matched route branch. Define its root type with `createRootRouteWithContext`, pass the concrete value when creating the router or provider, and extend it in `beforeLoad` when a child needs derived state. Loaders receive the merged context after the parent-to-child `beforeLoad` sequence completes.

Authentication checks belong in `beforeLoad` for protected routes. A pathless layout can protect a group without adding a URL segment. If the user is unauthenticated, throw a router redirect and include the current location when the login flow needs a safe return destination. The login route must not sit beneath the same protected layout, or the redirect can loop.

Context is not automatically reactive just because the application auth store changed. Pass the current auth state through the router integration and invalidate the router after a login, logout, or permission change so matching routes rerun their load lifecycle. A stale route context can leave protected UI visible or continue redirecting after a successful login.

Client-side guards improve navigation behavior but are not an authorization boundary for data. Loaders and server endpoints must enforce access independently. Do not place secrets in router context; client route context is application state, not secure server storage.

Use route context for stable dependencies such as a Query client, API facade, or auth interface. Avoid creating those dependencies inside every loader. When a child adds context, keep the addition narrow and typed so sibling routes do not appear to own values they never receive.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/authenticated-routes.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/router-context.md


