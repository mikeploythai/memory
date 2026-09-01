---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "errors, not-found results, and redirects"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/not-found-errors.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Errors, not-found results, and redirects

TanStack Router distinguishes ordinary errors, not-found control flow, and redirects. A route can define `errorComponent`, `notFoundComponent`, and pending UI. Errors raised during matching, `beforeLoad`, or loading are handled by the nearest applicable boundary. Components can also throw into a route boundary, but data failures are usually clearer when raised by the loader that owns the request.

Use `notFound()` when the requested resource or route-specific entity does not exist. It carries not-found metadata and can target the current route boundary or allow the router to select the appropriate parent. This is different from throwing a generic `Error`: not-found UI communicates a valid request with no matching resource, while error UI communicates a failed operation.

Use `redirect()` as control flow in `beforeLoad` or a loader. Supply a typed `to`, params, and search when redirecting within the application. A redirect can replace history when the intermediate URL should not remain. Throwing or returning redirect results must follow the API documented for the call site; do not catch them as ordinary failures and convert them into generic error messages.

Boundary placement is architectural. A root boundary supplies a final fallback, while route-level boundaries keep a failure inside a feature layout. Avoid a not-found route definition that accidentally shadows valid descendants. When authentication redirects preserve a requested destination, validate that destination before using it after login to avoid open redirects.

Reset or retry flows should cause the loader or match to run again rather than merely hiding the error component. Keep error messages safe for client rendering and log sensitive diagnostics through a separate channel.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/guide/not-found-errors.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/api/router/notFoundFunction.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/api/router/redirectFunction.md


