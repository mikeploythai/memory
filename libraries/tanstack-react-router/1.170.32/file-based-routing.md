---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "file-based routing"
source: "https://tanstack.com/router/latest/docs/quick-start"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32; moving React v1 docs"
---

# File-based routing with TanStack Router

TanStack Router's React documentation recommends file-based routing for most applications. The current documentation is a moving React v1 source; the package version recorded here is 1.170.32.

## Installation and requirements

```sh
npm install @tanstack/react-router
```

React and ReactDOM 18 or newer are required. TypeScript 5.3 or newer is recommended. A new Router-only project can be scaffolded with:

```sh
npx @tanstack/cli create --router-only
```

For an existing application, install the Router package and configure the official Router plugin or CLI so it can generate the route tree.

## Define a file route

Export the route as `Route`. The generator manages the literal path passed to `createFileRoute`.

```tsx
import { createFileRoute } from '@tanstack/react-router'

export const Route = createFileRoute('/')({
  loader: async () => ({ greeting: 'Hello' }),
  component: Home,
})

function Home() {
  const data = Route.useLoaderData()
  return <h1>{data.greeting}</h1>
}
```

Create the router with the generated route tree, pass it to `RouterProvider`, and register its type through module augmentation for end-to-end route type safety.

## Notes

- The `latest` documentation can change and should be rechecked after seven days for current-behavior work.
- Code-based routing is supported, but it is not the primary recommendation in the quick start.
- Do not hand-edit the generated route tree or generator-managed route path.

## Sources

- https://tanstack.com/router/latest/docs/installation/manual
- https://tanstack.com/router/latest/docs/guide/creating-a-router
