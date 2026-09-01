---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "manual setup and first build"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/build-from-scratch.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Manual setup and first build

This version-pinned Vite starting point follows the package metadata and basic example at the Start 1.168.30 release commit. Use Node 22.12 or newer. The same commit pairs Start 1.168.30 with Router 1.170.18; these packages are independently versioned.

```sh
mkdir my-start-app
cd my-start-app
npm init -y
```

Replace `package.json` with this minimal pinned version. Nitro supplies the production server output used by the `start` script.

```json
{
  "name": "my-start-app",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite dev",
    "build": "vite build && tsc --noEmit",
    "preview": "vite preview",
    "start": "node .output/server/index.mjs"
  },
  "dependencies": {
    "@tanstack/react-router": "1.170.18",
    "@tanstack/react-start": "1.168.30",
    "react": "19.0.0",
    "react-dom": "19.0.0"
  },
  "devDependencies": {
    "@types/node": "22.5.4",
    "@types/react": "19.0.8",
    "@types/react-dom": "19.0.3",
    "@vitejs/plugin-react": "6.0.1",
    "nitro": "3.0.260311-beta",
    "typescript": "6.0.2",
    "vite": "8.0.14"
  }
}
```

Install and retain the generated lockfile:

```sh
npm install
```

Create `tsconfig.json`. Keep `verbatimModuleSyntax` disabled; the exact guide warns that enabling it can leak server bundles into client bundles.

```json
{
  "include": ["**/*.ts", "**/*.tsx", "**/*.d.ts"],
  "compilerOptions": {
    "strict": true,
    "esModuleInterop": true,
    "jsx": "react-jsx",
    "module": "ESNext",
    "moduleResolution": "Bundler",
    "lib": ["DOM", "DOM.Iterable", "ES2022"],
    "isolatedModules": true,
    "resolveJsonModule": true,
    "skipLibCheck": true,
    "target": "ES2022",
    "forceConsistentCasingInFileNames": true,
    "noEmit": true
  }
}
```

Create `vite.config.ts`. Plugin order matters: Start precedes React. The exact basic example adds Nitro for a runnable production server.

```ts
import { tanstackStart } from '@tanstack/react-start/plugin/vite'
import viteReact from '@vitejs/plugin-react'
import { defineConfig } from 'vite'
import { nitro } from 'nitro/vite'

export default defineConfig({
  server: { port: 3000 },
  resolve: { tsconfigPaths: true },
  plugins: [tanstackStart({ srcDirectory: 'src' }), viteReact(), nitro()],
})
```

A minimal application then needs the three files provided in `routing.md`: `src/router.tsx`, `src/routes/__root.tsx`, and `src/routes/index.tsx`. Running the development server generates `src/routeTree.gen.ts`; never create or edit that generated file by hand.

Verify development with `npm run dev`, open `http://localhost:3000`, and confirm that the index route renders and `src/routeTree.gen.ts` appears. Verify production with `npm run build`; this also runs `tsc --noEmit`. Then run `npm run start`, load the same URL reported by the server, and exercise the server function from `server-functions.md`. A type-check alone is insufficient because route generation, import protection, and client/server bundling run through the build.

The upstream example's lockfile is not indexed here, so this page does not promise hermetic transitive dependency reproduction. Retain the `package-lock.json` produced by the first successful install. If installation resolves incompatible transitive versions, inspect the lockfile and installed artifacts, which are the final authority. Do not substitute Router 1.170.32 merely because that separate Memory corpus exists; the exact Start release commit used Router 1.170.18.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/build-from-scratch.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/examples/react/start-basic/package.json
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/examples/react/start-basic/tsconfig.json
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/examples/react/start-basic/vite.config.ts
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/packages/react-start/package.json

