---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "environment functions and import protection"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/environment-functions.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Environment functions and import protection

Environment functions make runtime intent explicit. Server-only functions hold implementations that must execute only on the server. Client-only functions protect browser-specific behavior. Isomorphic functions provide separate server and client implementations behind one call site. These tools are appropriate for storage adapters, logging, environment-specific APIs, and other behavior that should keep a shared interface without sharing an implementation.

Import protection addresses a different risk: whether code is allowed into a bundle at all. Start's server/client boundary conventions prevent forbidden modules from crossing into the wrong build. Use them for database drivers, filesystem access, private SDKs, and modules that read server credentials. A conditional expression inside an isomorphic module is not equivalent protection if the sensitive import is still statically reachable.

Keep imports flowing in the safe direction. Shared code should depend on pure types and runtime-neutral utilities. Client modules must not import a server implementation through an intermediate barrel file. Re-export chains can obscure the boundary, so put privileged modules in clearly named server-only files and keep shared entry points clean.

Environment helpers fail deliberately when used in the wrong runtime. Do not catch that failure and silently fall back to insecure behavior. If a feature genuinely needs both implementations, define both rather than reaching for a server function from a low-level shared utility without considering network and async behavior.

Server functions remain the network-call boundary for client-initiated privileged work. Environment functions choose a local implementation for the current runtime; they are not automatically RPC endpoints. Confusing the two can make browser code attempt to execute a server-only implementation.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/environment-functions.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/import-protection.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/code-execution-patterns.md


