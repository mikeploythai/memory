---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "greenfield routing and document shell"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/routing.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Greenfield routing and document shell

TanStack Start uses TanStack Router's file-based routing. After completing `build-from-scratch.md`, create `src/router.tsx`:

```tsx
import { createRouter } from '@tanstack/react-router'
import { routeTree } from './routeTree.gen'

export function getRouter() {
  return createRouter({
    routeTree,
    scrollRestoration: true,
  })
}
```

`getRouter` returns a new router instance so server requests do not share request-specific router state. `routeTree.gen.ts` is intentionally missing until the first development/build run.

Create the required document shell at `src/routes/__root.tsx`:

```tsx
import type { ReactNode } from 'react'
import {
  HeadContent,
  Outlet,
  Scripts,
  createRootRoute,
} from '@tanstack/react-router'

export const Route = createRootRoute({
  head: () => ({
    meta: [
      { charSet: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { title: 'TanStack Start app' },
    ],
  }),
  component: RootComponent,
})

function RootComponent() {
  return (
    <RootDocument>
      <Outlet />
    </RootDocument>
  )
}

function RootDocument({ children }: { children: ReactNode }) {
  return (
    <html>
      <head><HeadContent /></head>
      <body>{children}<Scripts /></body>
    </html>
  )
}
```

Omitting `Scripts` prevents the client JavaScript from loading correctly. Create `src/routes/index.tsx`:

```tsx
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/')({ component: Home })

function Home() {
  return <h1>TanStack Start is running</h1>
}
```

Run `npm run dev`, open `http://localhost:3000`, and confirm both the heading and generated `src/routeTree.gen.ts`. The path passed to `createFileRoute` is managed by the Router plugin or CLI; do not hand-edit it or the generated route tree after moving files.

Nested filenames produce nested component trees. For example, a layout route for posts and a dynamic child for `$postId` render below the root document for `/posts/123`. Use the generated route APIs for typed params, loader data, search parameters, and navigation.

The Start routing guide is a bridge into Router. This release commit contains Router 1.170.18. Memory's separate Router corpus is 1.170.32, so do not transfer its implementation-sensitive behavior without checking the installed 1.170.18 artifacts or an exact matching source.

Verify the routing setup by running the development server, confirming generation of `routeTree.gen.ts`, loading `/`, and adding a second route to confirm regeneration. Then run the production build so both client and server route bundles are exercised.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/routing.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/build-from-scratch.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/examples/react/start-basic/src/router.tsx
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/examples/react/start-basic/src/routes/index.tsx

