---
library: "@tanstack/react-start"
version: "1.168.49"
topic: "bootstrap and build from scratch"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/start/framework/react/build-from-scratch.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.49; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Bootstrap and build from scratch

TanStack Start is a Router-powered full-stack React framework. The official
overview still labels it Release Candidate even though `@tanstack/react-start`
1.168.49 is published under npm's stable `latest` dist-tag.

## Scaffold or clone

Interactive project creation:

```sh
npx @tanstack/cli@latest create
```

The `@latest` dist-tag is mutable. This command records the official discovery
path, not a release-pinned scaffold for `@tanstack/react-start@1.168.49`.

Clone the official basic example:

```sh
npx gitpick TanStack/router/tree/main/examples/react/start-basic start-basic
cd start-basic
npm install
npm run dev
```

The example command tracks the mutable `main` branch. Its files and dependency
versions can change independently of this Memory version directory, so it is
discovery evidence rather than a reproducible `1.168.49` bootstrap.

## Manual initialization

```sh
mkdir myApp
cd myApp
npm init -y
npm i @tanstack/react-start @tanstack/react-router
npm i react react-dom
npm i -D vite @vitejs/plugin-react
npm i -D typescript @types/react @types/react-dom @types/node
```

These official install commands are unpinned. This page does not retain an
exact compatible version for every companion package, so the commands may
resolve a dependency set newer than the release identified in the frontmatter.

The documented TypeScript baseline uses `jsx: react-jsx`, Bundler module
resolution, ESNext modules, ES2022 target, `skipLibCheck`, and
`strictNullChecks`. Keep `verbatimModuleSyntax` disabled; the guide warns that
enabling it can leak server bundles into client bundles.

This is a settings summary, not a complete `tsconfig.json`. The full file is
not retained in this bounded batch.

## Scripts and Vite configuration

```json
{
  "type": "module",
  "scripts": {
    "dev": "vite dev",
    "build": "vite build"
  }
}
```

```ts
// vite.config.ts
import { defineConfig } from 'vite'
import { tanstackStart } from '@tanstack/react-start/plugin/vite'
import viteReact from '@vitejs/plugin-react'

export default defineConfig({
  server: { port: 3000 },
  resolve: { tsconfigPaths: true },
  plugins: [tanstackStart(), viteReact()],
})
```

The Start plugin must precede the React plugin.

## Required application files

```text
src/
├── router.tsx
├── routeTree.gen.ts
└── routes/
    ├── __root.tsx
    └── index.tsx
```

`routeTree.gen.ts` is generated on the first Start run.

```tsx
// src/router.tsx
import { createRouter } from '@tanstack/react-router'
import { routeTree } from './routeTree.gen'

export function getRouter() {
  return createRouter({ routeTree, scrollRestoration: true })
}
```

The root route must render a full document containing `HeadContent`, an
`Outlet`, and `Scripts`. The first route can call a `createServerFn` from its
loader and render the returned value.

The complete contents of `src/routes/__root.tsx` and `src/routes/index.tsx` are
not retained here. Because those required files and the full TypeScript config
are missing, the manual setup is not a self-contained runnable application.

## Verification

The official verification steps are recorded below, but they have not been
reproduced from this partial Memory bootstrap alone.

```sh
npm run dev
```

Open `http://localhost:3000`. The documented scratch example renders a counter;
clicking its button updates a server-side file and invalidates the router.

```sh
npm run build
```

The build script is explicit, but the scratch page does not state one exact
artifact listing or production-start command for every supported adapter.
Deployment verification is provider-specific.

## Readiness

Greenfield React/Vite bootstrap is **partial**. The retained material identifies
the commands, scripts, Vite plugin order, required filenames, router factory,
and expected checks. It does not retain complete route-file contents, a complete
TypeScript configuration, exact companion-package versions, or an immutable
copy of the basic example. Consult a release-pinned first-party source before
using this page to create a new application.

## Sources

- https://tanstack.com/start/latest/docs/framework/react/overview.md
- https://tanstack.com/start/latest/docs/framework/react/getting-started.md
- https://tanstack.com/start/latest/docs/framework/react/examples/start-basic.md
- https://tanstack.com/start/latest/docs/framework/react/guide/routing.md
