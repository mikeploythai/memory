---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "environment variables and secret handling"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/environment-variables.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Environment variables and secret handling

Environment variables belong to either server-only configuration or deliberately public client configuration. Variables exposed through the client build are compiled into or otherwise delivered with browser assets and must be treated as public. Naming conventions that mark a variable as client-visible do not encrypt it.

Read secrets only behind server functions, server routes, server middleware, or protected server modules. Do not read a secret in a route loader merely because the first load happens during SSR; loaders also run in the browser during client navigation. Do not return a secret from a server function or loader result, because serialized output becomes visible to the caller.

Validate required configuration during server startup or at a clear server boundary. Convert strings into the expected boolean, number, URL, or enum rather than relying on JavaScript truthiness. Fail with a diagnostic that names the missing configuration but does not print the secret value.

Client-visible configuration is suitable for public origins, analytics identifiers intended for browsers, and feature flags with no confidentiality requirement. Even public variables should be normalized in one module so application code does not depend directly on build-tool details.

Deployment environments can supply variables differently. Keep access behind a small configuration interface and verify the hosting runtime's documented mechanism. A local `.env` workflow does not guarantee the same variables exist in a production worker or serverless environment.

Import protection is part of secret handling. If a shared barrel re-exports a server configuration module, a client import can cross the boundary unintentionally. Keep server configuration in a server-only path and audit the serialized data returned from that path.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/environment-variables.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/import-protection.md


