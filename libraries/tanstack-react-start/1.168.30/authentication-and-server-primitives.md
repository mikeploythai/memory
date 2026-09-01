---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "authentication and server-side auth primitives"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/authentication-overview.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Authentication and server-side auth primitives

Authentication has separate server and route concerns. The server establishes identity from a session, cookie, token, or provider callback. Protected server functions and server routes verify that identity and authorize the requested operation. Router guards then use a safe representation of auth state to redirect users and shape navigation.

Read and write session material through server-side request primitives. Cookies carrying session identifiers need deliberate security attributes, expiry, and same-site behavior. Do not expose a session secret or provider credential through loader data, environment variables marked for the client, or router context. Treat all cookie and header values as untrusted until verified.

Server middleware can resolve the current user once and attach a typed identity to request context. Downstream handlers still need operation-specific authorization; “logged in” does not imply access to every tenant or record. Derive tenant and user identity from the verified session, not from a client-provided field.

For route protection, use `beforeLoad` and a pathless protected layout when multiple routes share the rule. Keep the login and callback routes outside that layout. After login or logout, invalidate router state so guards and loaders rerun with the new identity. Validate return destinations to prevent an open redirect.

Client state is a UX cache, not the source of authority. A user can call a server endpoint without visiting the guarded route. Every privileged server boundary must repeat or inherit server authorization.

Provider integrations add callback, token, and refresh behavior, but the same boundary rules apply. Keep provider-specific credentials server-only, verify callback state, and store only the minimum safe user representation in client-visible data.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/authentication-overview.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/authentication-server-primitives.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/authentication.md


