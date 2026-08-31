---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "typed server functions"
source: "https://tanstack.com/start/latest/docs/framework/react/guide/server-functions"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30; moving docs labeled Release Candidate"
---

# Typed server functions with TanStack Start

TanStack Start server functions define server-only handlers that application code can call as typed, same-origin RPC operations.

## Status and setup

The official overview describes Start as Release Candidate software: feature-complete with an API considered stable, but not yet presented as generally stable. The moving docs and package numbering do not use the same visible version label, so retain this caveat when implementing against 1.168.30.

Scaffold a project with:

```sh
npx @tanstack/cli@latest create
```

A manual setup installs Start and Router together:

```sh
npm install @tanstack/react-start @tanstack/react-router
```

## Define and call a server function

```tsx
import { createServerFn } from '@tanstack/react-start'

export const getServerTime = createServerFn().handler(async () => {
  return new Date().toISOString()
})

const serverTime = await getServerTime()
```

The default method is GET. Use `createServerFn({ method: 'POST' })` for writes, and validate all input crossing the client/server boundary.

## Notes

- Server functions are application RPC endpoints, not a replacement for a public or cross-origin API.
- Apply authentication and authorization inside every handler that accesses private data.
- Route loaders are isomorphic and are not inherently server-only.
- React Server Components remain experimental.
- If an application supplies a custom `src/start.ts`, follow the current CSRF middleware guidance.

## Sources

- https://tanstack.com/start/latest/docs/framework/react/overview
- https://tanstack.com/start/latest/docs/framework/react/getting-started
- https://tanstack.com/start/latest/docs/framework/react/build-from-scratch
