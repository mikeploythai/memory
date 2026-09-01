---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "server functions"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-functions.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Server functions

Server functions define an RPC-style boundary that application code can call with normal TypeScript ergonomics while Start executes the implementation on the server. Create the function with `createServerFn`, choose the HTTP method when needed, add input validation, and place privileged work in the server handler. Calls made during SSR can execute on the server; browser calls are transported to the generated endpoint.

Treat every call as an untrusted request. TypeScript types disappear at the network boundary, so validate runtime input before using it. Authentication and authorization must run inside the server boundary or server middleware. A client route guard is not enough. Do not accept a user or tenant identifier from input when it should come from the authenticated request context.

Arguments and return values cross a serialization boundary. Return data intended for the client, not database handles, request objects, functions, or secrets. Redirect and not-found control flow can integrate with Router when raised through the documented Start/Router APIs. Ordinary errors should be sanitized for client display while server logs retain appropriate diagnostics.

Server functions can be called from route loaders, components through the React integration, and other server code. A loader remains isomorphic even when it calls a server function; the privileged implementation is protected because it is behind the function boundary. Keep non-idempotent work on an appropriate method and design retries or repeated submissions safely.

Use middleware for cross-cutting request context, authentication, or logging rather than duplicating it in every function. Keep each function focused on one operation so validation, permissions, cache invalidation, and failure behavior remain easy to inspect.

## Minimal typed server function

After the greenfield routing setup, replace `src/routes/index.tsx` with this exact-release pattern:

```tsx
import { createFileRoute } from '@tanstack/react-router'
import { createServerFn } from '@tanstack/react-start'

const getServerTime = createServerFn({ method: 'GET' }).handler(() => {
  return new Date().toISOString()
})

export const Route = createFileRoute('/')({
  loader: () => getServerTime(),
  component: Home,
})

function Home() {
  const serverTime = Route.useLoaderData()
  return <p>Server time: {serverTime}</p>
}
```

The handler's inferred return type flows through the server-function call, route loader, and `useLoaderData`. For input, chain `.validator((input: Input) => validatedInput)` before `.handler(({ data }) => ...)`; runtime validation and authorization still belong inside the server boundary.

Run `npm run dev`, load `/`, and confirm a server timestamp renders. Refresh and confirm it changes. Then run `npm run build` followed by `npm run start` and repeat the check against the production server. The production build must also succeed with import protection enabled; build-time import-protection failures mean restricted code survived tree shaking.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-functions.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/examples/react/start-counter/src/routes/index.tsx

