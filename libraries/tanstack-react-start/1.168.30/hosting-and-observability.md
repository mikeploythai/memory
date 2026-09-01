---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "hosting and observability"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/hosting.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Hosting and observability

Deploy the output produced for the selected Start build and hosting integration. A host must support the runtime capabilities the application uses: SSR and server functions require request execution, streaming requires compatible response handling, and SPA fallback requires rewriting application paths to the client shell. Static assets should be served from the generated asset output with their emitted names and cache policy.

Do not assume an adapter or configuration for another framework applies to Start. Follow the exact Start hosting guide and the selected provider's current instructions. Runtime differences matter for Node APIs, workers, filesystem access, environment variables, request limits, and streaming. Server-only application modules must use APIs available in the target runtime.

Check direct route loads in production, not only client navigation. Verify asset URLs, base paths, server routes, server functions, redirects, error status codes, and streaming responses. If a CDN sits in front of the app, separate immutable asset caching from personalized HTML and API responses. Never cache authenticated HTML across users.

Observability should cover the request lifecycle, route/server-function failures, and deployment runtime without leaking secrets or personal data. Attach request identifiers through server middleware or the supported instrumentation boundary. Record durations and failure classes around server work while preserving the original response and error behavior.

Client and server telemetry need different initialization. Keep server exporters and credentials behind import protection; expose only public client configuration to browser monitoring. Source maps and error payloads require deliberate access controls.

Observability wrappers must not consume streams, call handlers twice, or convert redirects into generic errors. Test instrumentation with successful HTML, streamed HTML, server-function failure, server-route responses, and aborted requests.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/hosting.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/observability.md


