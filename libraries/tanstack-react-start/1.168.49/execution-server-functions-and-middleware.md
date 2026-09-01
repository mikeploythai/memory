---
library: "@tanstack/react-start"
version: "1.168.49"
topic: "execution model, server functions, and middleware"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/start/framework/react/guide/execution-model.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.49; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Execution model, server functions, and middleware

Start code is isomorphic by default. Route loaders run during server rendering
and again in the browser during client navigation. A loader is not a server-only
security boundary.

## Choose the correct boundary

| API | Purpose | Client behavior |
|---|---|---|
| `createServerFn` | Typed RPC-like server work | Calls the server implementation |
| `createServerOnlyFn` | Utility that must run only on the server | Throws if called in the client |
| `createClientOnlyFn` | Utility that must run only in the browser | Throws if called on the server |
| `createIsomorphicFn` | Explicit server and client implementations | Runs the environment-specific branch |
| `ClientOnly` | Defer component output to the client | Renders after client hydration |

## Server function

```ts
import { createServerFn } from '@tanstack/react-start'

type ProjectInput = { id: string }

export const getProject = createServerFn({ method: 'GET' })
  .validator((input: ProjectInput) => input)
  .handler(async ({ data }) => {
    return database.projects.find(data.id)
  })
```

Call server functions from route loaders, components through `useServerFn`,
event handlers, or other server functions. Static imports are transformed into
client-callable stubs. The docs warn against dynamically importing server
functions because that can interfere with bundler transformation.

Keep server-only helpers separate from shared validation and function wrappers:

```text
src/utils/
├── projects.functions.ts
├── projects.server.ts
└── schemas.ts
```

The `.functions.ts` module exports `createServerFn` wrappers. `.server.ts`
contains database, filesystem, or secret-bearing implementation code.

## Middleware

Start distinguishes request middleware from server-function middleware. Both
can add context through `next({ context })`; server-function middleware may
also transfer selected context between client and server.

```ts
import { createMiddleware } from '@tanstack/react-start'

const requireUser = createMiddleware().server(async ({ next, context }) => {
  const user = await readCurrentUser()
  if (!user) throw new Error('Unauthorized')
  return next({ context: { ...context, user } })
})
```

Global middleware is configured through the Start instance. Middleware order,
validator order, client hooks, and server handlers affect which context and
headers are visible at each step.

## Server routes

Use server routes for externally callable HTTP endpoints. Use server functions
for typed calls owned by the Start application. Server routes must handle their
HTTP contract directly; they are not interchangeable with route loaders.

## Environment and import protection

- Only expose client-safe environment values through the documented public
  mechanism; a `VITE_` prefix makes values client-visible.
- Do not read secrets in an isomorphic route loader.
- Import protection can catch server-only modules entering client graphs, but
  it does not excuse placing secrets in shared modules.
- Dead-code elimination is a build optimization, not an authorization layer.

## Failure modes

- Treating loaders as server-only can expose secrets in browser navigation.
- Importing database code from a shared module can pull it into the wrong graph.
- Using request middleware where server-function middleware is required changes
  its scope.
- Returning unvalidated client input to a handler defeats the typed boundary.
- Throwing a generic error for expected authorization behavior may bypass the
  application's intended redirect or response policy.

## Sources

- https://tanstack.com/start/latest/docs/framework/react/guide/server-functions.md
- https://tanstack.com/start/latest/docs/framework/react/guide/middleware.md
- https://tanstack.com/start/latest/docs/framework/react/guide/server-routes.md
- https://tanstack.com/start/latest/docs/framework/react/guide/import-protection.md
- https://tanstack.com/start/latest/docs/framework/react/guide/environment-variables.md
- https://tanstack.com/start/latest/docs/framework/react/guide/code-execution-patterns.md
