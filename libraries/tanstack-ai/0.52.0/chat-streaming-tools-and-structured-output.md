---
library: "@tanstack/ai"
version: "0.52.0"
topic: "chat streaming, tools, and structured output"
source: "https://github.com/TanStack/ai/blob/b899fe5328f2907e5abbaa9c11b8f486caec229f/docs/chat/streaming.md"
retrieved_at: "2026-08-31"
source_ref: "b899fe5328f2907e5abbaa9c11b8f486caec229f"
---

# Chat streaming, tools, and structured output

This page maps the core chat workflow for TanStack AI `0.52.0`. It keeps the
server activity, transport, tool execution, and structured-output layers
separate because each has different trust and lifecycle rules.

## Chat activity

`chat()` accepts a provider adapter, model messages, optional system prompts,
tools, middleware, and an agent-loop strategy. The core API example uses:

```ts
import { chat, maxIterations } from '@tanstack/ai'
import { openaiText } from '@tanstack/ai-openai'

const stream = chat({
  adapter: openaiText('gpt-5.2'),
  messages: [{ role: 'user', content: 'Hello!' }],
  systemPrompts: ['You are a helpful assistant'],
  agentLoopStrategy: maxIterations(20),
})
```

The adapter controls provider-native model options and capabilities. Generic
sampling options were moved to provider-native `modelOptions` before this
release; see the migration page rather than using root-level `temperature`,
`topP`, or `maxTokens`.

## Streaming layers

The documentation divides streaming into these concerns:

| Concern | Official guide |
|---|---|
| Produce and consume chat streams | `docs/chat/streaming.md` |
| Select SSE, HTTP, RPC, XHR, or server-function transport | `docs/chat/connection-adapters.md` |
| Understand emitted event shapes | `docs/chat/stream-events.md` |
| Control repeated model/tool turns | `docs/chat/agentic-cycle.md` |
| Preserve reasoning content | `docs/chat/thinking-content.md` |
| Queue user messages | `docs/chat/queueing.md` |

Do not treat transport chunks as plain text by default. TanStack AI streams
typed events for text, tools, reasoning, usage, structured output, and custom
events.

## Tool boundaries

The guide corpus distinguishes:

- server tools, executed in the trusted server environment;
- client tools, executed by the application client;
- provider tools, executed by the upstream model provider;
- tools that require approval before execution;
- lazily discovered tools and MCP-provided tools.

Use `toolDefinition()` for a typed tool declaration. Keep input and output
schemas with the tool and validate at the execution boundary. Tool approval is
not equivalent to ordinary execution; approval requests must survive the
transport and resume path.

Managed MCP support can discover clients' tools at run start. The documented
`chat({ mcp: { clients, connection, lazyTools, onDiscoveryError } })` shape
controls discovery and connection lifetime. Duplicate discovered names can
raise `MCPDuplicateToolNameError`.

## Structured output

Structured output has distinct documented workflows:

1. One-shot extraction.
2. Streaming partial output for a UI.
3. Multi-turn structured chat.
4. Structured output combined with tools.
5. Harness-agent output.

When `outputSchema` is supplied, use the schema-inferred result type. Streaming
structured output emits raw JSON deltas and a terminal typed custom event. Do
not parse incomplete JSON with ordinary `JSON.parse()`.

In multi-turn clients, structured output belongs to the assistant message that
produced it. Consumers should read the typed structured-output part instead of
assuming a single global result slot or filtering a text part containing JSON.

## Common failure modes

- Mixing `UIMessage` and provider-native message shapes without the documented
  conversion helpers.
- Executing provider-owned tools again on the application server.
- Dropping reasoning or provider metadata needed for a follow-up turn.
- Using root-level sampling options removed by the `modelOptions` migration.
- Treating approval, interrupt, and ordinary tool-result events as equivalent.
- Closing an MCP connection that was intentionally configured as keep-alive.

## Coverage limits

This draft records the documented architecture and verified `chat()` call
shape. It does not reproduce every `StreamChunk` variant, connection-adapter
signature, tool schema example, or structured-output event interface. Use the
generated reference for symbol-level work.

## Sources

- https://tanstack.com/ai/latest/docs/chat/streaming.md
- https://tanstack.com/ai/latest/docs/chat/connection-adapters.md
- https://tanstack.com/ai/latest/docs/chat/stream-events.md
- https://tanstack.com/ai/latest/docs/chat/agentic-cycle.md
- https://tanstack.com/ai/latest/docs/tools/tools.md
- https://tanstack.com/ai/latest/docs/tools/tool-architecture.md
- https://tanstack.com/ai/latest/docs/tools/mcp-managed.md
- https://tanstack.com/ai/latest/docs/structured-outputs/overview.md
- https://tanstack.com/ai/latest/docs/structured-outputs/streaming.md
- https://tanstack.com/ai/latest/docs/structured-outputs/multi-turn.md
