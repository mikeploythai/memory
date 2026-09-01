---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "execution model and server-client code boundaries"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/execution-model.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Execution model and server-client code boundaries

TanStack Start code is isomorphic by default. Ordinary modules can be included in both server and client bundles, and route loaders run on the server for the initial request and in the browser during client navigation. A loader is therefore not a server-only boundary. Importing a database client, filesystem API, private environment value, or privileged service into ordinary route code can break the client build or expose implementation details.

Use server functions for callable server-only work and environment functions for code whose implementation differs by runtime. Server-only and client-only helpers can enforce that a function is called in the intended environment. `ClientOnly` defers browser-dependent rendering until the client is available, but it does not turn imported code into server-only code.

Think about both execution and bundling. A runtime branch such as checking for `window` may avoid executing a statement on the server, but import protection is still needed when the module itself must never enter the other bundle. Keep server dependencies behind a recognized boundary and let Start's build transform separate them.

Route `beforeLoad` and loaders can run more than once across SSR, hydration, preloads, and navigation. They should not perform an unguarded non-idempotent side effect. Use server functions for mutations, validate their input, and enforce authorization at that boundary.

When behavior must exist in both environments, isolate the shared pure logic and supply small server/client adapters for storage, headers, browser APIs, or credentials. This makes the execution location visible and keeps secrets out of values serialized to the browser.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/execution-model.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/code-execution-patterns.md


