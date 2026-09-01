---
library: "@tanstack/react-start"
version: "1.168.49"
topic: "authentication, migration, and API gaps"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/start/framework/react/guide/authentication-overview.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.49; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Authentication, migration, and API gaps

Authentication in Start spans server primitives, request middleware, server
functions, Router context, protected routes, cookies or sessions, and provider
integration. Client route guards alone do not protect server data.

## Authentication boundaries

1. Read and verify credentials on the server.
2. Put trusted identity into request or server-function context.
3. Enforce authorization again at server functions and server routes.
4. Expose only the client-safe user shape to Router context.
5. Redirect or return an HTTP response according to the caller's boundary.

```ts
import { createServerFn } from '@tanstack/react-start'

export const getCurrentUser = createServerFn({ method: 'GET' }).handler(
  async () => {
    const session = await readVerifiedSession()
    return session ? { id: session.user.id, name: session.user.name } : null
  },
)
```

Never return session secrets, raw tokens, password material, or private provider
responses to the client. Validation establishes input shape; authorization
establishes whether the caller may perform the operation.

## Data and databases

Database clients and credentials belong in server-only modules. Call them from
server functions, server routes, or request middleware. An isomorphic loader
must call a server boundary rather than importing the database client directly.

The docs include provider-oriented authentication examples and database
guidance, but examples are not a substitute for provider-specific threat
models, cookie settings, key rotation, CSRF controls, and deployment secrets.

## Migration from Next.js

The official migration page is the only completed framework migration listed in
the Start index. Treat migration as an architectural mapping:

- Move navigation and URL state to TanStack Router route definitions.
- Replace framework-specific server actions with Start server functions where
  the typed application-call model fits.
- Replace API routes with Start server routes where an HTTP endpoint is needed.
- Rebuild middleware using Start's request and server-function middleware.
- Recreate document metadata, SSR, static output, and deployment configuration
  using Start's rendering and hosting guides.
- Re-evaluate environment variables and server-only imports.

Do not mechanically rename imports. Next.js server components, caching,
filesystem conventions, middleware, and deployment behavior have different
semantics.

The Getting Started page lists Remix 2 / React Router 7 Framework Mode migration
as “coming soon.” That migration is a documented gap, not an implied supported
procedure.

## API coverage

Start has no consolidated API section in the official `llms.txt` index. The
documented public surface is distributed across guides and package source.
Important families include:

- `createServerFn` and `useServerFn`
- `createMiddleware`
- `createStart`
- `createServerOnlyFn`, `createClientOnlyFn`, and `createIsomorphicFn`
- Start client and server entry components
- Request, response, context, streaming, and static-server-function behavior
- Re-exported Router APIs from the React Start entry package

For exact signatures, inspect the package declarations at the pinned release.
Do not assume the independently versioned client-core, server-core, and
plugin-core packages share `1.168.49`.

## Failure modes

- A client redirect without server authorization leaves the data path exposed.
- Importing a database client into a loader risks client-bundle leakage.
- Treating validation as authorization accepts well-formed unauthorized input.
- Copying Next.js caching assumptions into Start can change data freshness.
- Treating all `@tanstack/start-*` packages as one version can produce an
  impossible dependency set.

## Sources

- https://tanstack.com/start/latest/docs/framework/react/guide/authentication-server-primitives.md
- https://tanstack.com/start/latest/docs/framework/react/guide/authentication.md
- https://tanstack.com/start/latest/docs/framework/react/guide/databases.md
- https://tanstack.com/start/latest/docs/framework/react/migrate-from-next-js.md
- https://tanstack.com/start/latest/docs/framework/react/guide/server-routes.md
- https://github.com/TanStack/router/tree/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/packages/react-start
