---
library: "@tanstack/react-start"
version: "1.168.49"
topic: "rendering, SSR, and hosting"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/start/framework/react/guide/selective-ssr.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.49; commit a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Rendering, SSR, and hosting

Initial requests render matched routes on the server by default, then hydrate
in the browser. Later client navigation runs route work in the browser.

## Selective SSR

Configure route-level `ssr` behavior:

| Value | Server data work | Server component rendering |
|---|---|---|
| `true` | `beforeLoad` and `loader` run | rendered and hydrated |
| `false` | skipped | skipped; client renders route |
| `'data-only'` | route data runs | component markup omitted |

The default is `true`. A Start instance can set a different default.

```ts
// src/start.ts
import { createStart } from '@tanstack/react-start'

export const startInstance = createStart(() => ({
  defaultSsr: false,
}))
```

Use selective SSR when route code depends on browser-only APIs or when the
server should load data without rendering a component. SPA mode disables the
server route execution/rendering path for the application rather than selecting
behavior route by route.

## Hydration

Server and client output must agree. Browser globals, current time, random
values, locale differences, malformed HTML, and client-only persisted state can
cause hydration errors. Defer browser-only output or pass stable server data to
the client rather than suppressing unexplained mismatches.

`HeadContent` belongs in the document head and `Scripts` in the body. Removing
the scripts prevents the rendered document from becoming interactive.

## Static output

The rendering corpus includes static prerendering, incremental static
regeneration for the React adapter, deferred hydration, early hints, custom
client/server entry points, and CDN asset URLs. These features have different
runtime and provider requirements; do not treat them as one deployment mode.

## Build

The scratch setup defines:

```json
{
  "scripts": {
    "dev": "vite dev",
    "build": "vite build"
  }
}
```

Run `npm run build` before provider deployment. The selected hosting adapter
determines the server entry, output layout, preview command, and deploy command.

## Cloudflare example

The official hosting guide installs Cloudflare's Vite plugin and Wrangler,
places the Cloudflare plugin before Start, and defines a Worker entry.

```sh
pnpm add -D @cloudflare/vite-plugin wrangler
pnpm run deploy
```

The documented scripts use `vite build && tsc --noEmit` for the build and
`wrangler deploy` for deployment. The guide's sample `compatibility_date` is a
provider setting that should be reviewed rather than copied indefinitely.

## Other hosting paths

The official page also documents Netlify and links provider-specific setup.
Start supports Vite and Rsbuild, but support for a build tool does not mean the
same output runs unchanged on every serverless, edge, or Node runtime.

## Failure modes

- `ssr: false` changes loader execution as well as component rendering.
- Accessing `localStorage` during SSR causes runtime or hydration failures.
- A singleton QueryClient on the server can leak data across requests.
- Copying provider configuration without its runtime adapter can produce a
  successful build that cannot start.
- Suppressing hydration warnings hides differences rather than correcting them.

## Gaps

The docs do not provide one universal production-start command or artifact
shape because hosting targets differ. A deployment page must be pinned with its
provider plugin, runtime, and dated provider configuration.

## Sources

- https://tanstack.com/start/latest/docs/framework/react/guide/hydration-errors.md
- https://tanstack.com/start/latest/docs/framework/react/guide/spa-mode.md
- https://tanstack.com/start/latest/docs/framework/react/guide/static-prerendering.md
- https://tanstack.com/start/latest/docs/framework/react/guide/isr.md
- https://tanstack.com/start/latest/docs/framework/react/guide/hosting.md
- https://tanstack.com/start/latest/docs/framework/react/guide/client-entry-point.md
- https://tanstack.com/start/latest/docs/framework/react/guide/server-entry-point.md
