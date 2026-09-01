---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "overview and package choice"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/overview.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Overview and package choice

TanStack Start is a full-stack React framework built on TanStack Router and either Vite or Rsbuild. At this release it provides full-document server rendering, streaming, server and API routes, typed server functions, request middleware, separate client/server builds, and deployment adapters. The exact-tag documentation describes Start as release-candidate software: feature-complete with an API considered stable, but not guaranteed bug-free.

Choose Start when the application needs framework-managed server rendering, server functions, backend routes, middleware, full-stack builds, or a shared client/server deployment model. Choose `@tanstack/react-router` alone when the project is a client-side application and those full-stack features are known to be unnecessary. Start uses Router for all routing, so a Start project normally installs both packages and follows Router's file-based routing model.

The framework does not hide its build system. A greenfield project also needs React, React DOM, TypeScript for the documented setup, and either Vite with its React plugin or Rsbuild with its React plugin. Package versions in the monorepo move independently. At the Start 1.168.30 release commit, the Router package is 1.170.18 and the exact basic example uses that pairing. Start requires Node 22.12 or newer, React/React DOM 18 or newer, and Vite 7 or newer when Vite is selected.

React Server Components are experimental at this release and should not be treated as a default project requirement. A conventional greenfield project can use server-rendered React, route loaders, server functions, and streaming without enabling RSC.

Continue with `getting-started.md` to choose a scaffold path. Use `build-from-scratch.md` when exact configuration matters or an existing toolchain must be wired manually. The first application route and generated route tree are covered in `routing.md`.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/overview.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/build-from-scratch.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/packages/react-start/package.json
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/packages/react-router/package.json

