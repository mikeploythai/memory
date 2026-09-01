---
library: "@tanstack/ai"
version: "0.52.0"
topic: "server chat and transports"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/getting-started/quick-start-server.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Server chat and transports

The server-only path uses the same core `chat()` runtime without a framework hook. A route, worker, script, or service supplies an adapter, normalized messages, optional tools, and loop policy, then exposes the resulting stream through HTTP, server-sent events, WebSocket, or an application-owned connection. Transport code carries AG-UI events; it does not own the model loop.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Authenticate and authorize the route before starting a provider request.
- Use the response helper that matches the chosen transport and propagate request cancellation into the model run.
- Normalize inbound messages at the boundary and keep application metadata namespaced and validated.
- Treat reconnect and resume as explicit protocols; ordinary streaming alone does not guarantee durability.

## Constraints and failure modes

- Returning a raw async iterable from a framework route without the correct response wrapper can lose headers, framing, or cancellation.
- Do not trust client-supplied tool results, system prompts, model IDs, or provider options without validation.
- SSE, HTTP streams, and WebSockets have different resume and proxy behavior; changing transport is not merely renaming a helper.

## Retrieval cues

Use this page when work mentions server chat and transports, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/getting-started/quick-start-server.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/chat/connection-adapters.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/api/ai.md

