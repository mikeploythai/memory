---
library: "@tanstack/ai"
version: "0.52.0"
topic: "react streaming chat"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/getting-started/quick-start.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# React streaming chat

TanStack AI separates the server-side model run from the client-side conversation state. The server creates a `chat()` stream with a provider adapter and returns an AG-UI-compatible response. The React client consumes that stream through `useChat` and a connection adapter. Messages are structured UI records rather than plain strings: content, reasoning, tool calls, tool results, and structured output can arrive as distinct parts.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Keep provider credentials and server tools behind the server route; send only the message and application context the route needs.
- Choose a connection adapter explicitly and preserve message IDs when persisting or resuming a thread.
- Render message parts by their discriminant instead of assuming every assistant message contains one text string.
- Handle abort, error, finish, and interrupt states in the UI; a stream ending is not the same as a successful model turn.

## Constraints and failure modes

- Do not call provider adapters directly from browser code when that would expose a secret.
- Do not flatten tool or reasoning parts into text before the client has processed their lifecycle events.
- A React hook version that does not match the core/client packages can produce incompatible event or message types.

## Retrieval cues

Use this page when work mentions react streaming chat, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/getting-started/quick-start.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/chat/streaming.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/api/ai-react.md

