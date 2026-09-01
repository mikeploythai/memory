---
library: "@tanstack/ai"
version: "0.52.0"
topic: "migration and API map"
source: "https://github.com/TanStack/ai/blob/b899fe5328f2907e5abbaa9c11b8f486caec229f/docs/migration/migration.md"
retrieved_at: "2026-08-31"
source_ref: "b899fe5328f2907e5abbaa9c11b8f486caec229f"
---

# TanStack AI migration and API map

Use this page to route a migration or symbol lookup. It does not replace the
source- and target-version pages required for an actual upgrade.

## Migration guides in the release

| Guide | Scope |
|---|---|
| `migration/migration.md` | General TanStack AI migration guidance |
| `migration/migration-from-vercel-ai.md` | Move from Vercel AI SDK concepts and APIs |
| `migration/ag-ui-compliance.md` | Adopt the AG-UI client-to-server request shape |
| `migration/sampling-options-to-model-options.md` | Move generic sampling keys into provider-native options |
| `interrupts/migration.md` | Move approval flows to interrupt continuations |
| `persistence/migrations.md` | Evolve persisted records and adapter behavior |

## Sampling-options migration

Root-level `temperature`, `topP`, and `maxTokens` were removed from `chat()`,
`ai()`, and `generate()` configuration. Use provider-native keys under
`modelOptions`.

Documented examples include:

| Provider | Representative option keys |
|---|---|
| OpenAI Responses | `temperature`, `top_p`, `max_output_tokens` |
| Anthropic | `temperature`, `top_p`, `max_tokens` |
| Gemini | `temperature`, `topP`, `maxOutputTokens` |
| Groq | `temperature`, `top_p`, `max_completion_tokens` |
| Ollama | nested `options.temperature`, `options.top_p`, `options.num_predict` |

Middleware that previously changed generic sampling fields must update
`config.modelOptions`. The official changelog also documents a repository
codemod command, but this draft does not reproduce it because its exact script
availability was not verified at the pinned release checkout.

## AG-UI migration

The compliant client request body uses AG-UI `RunAgentInput` fields including
thread, run, state, messages, tools, context, and forwarded properties. Server
endpoints should use the documented request-body conversion and tool-merging
helpers. Upgrade the core and client packages together while retaining their
independent version numbers.

## Package API summaries

The hosted API section has package pages for:

- `@tanstack/ai` and `@tanstack/ai-client`;
- React, Vue, Solid, Svelte, and Preact bindings;
- Angular and Octane bindings.

Start with the core package summary for installation and common functions, then
use the generated symbol reference for exact signatures.

## Generated reference areas

The `0.52.0` release contains 460 generated reference pages grouped as:

- classes such as stream processors, strategies, parsers, stores, and errors;
- functions for chat, generation, tools, schemas, transports, interrupts,
  replay, cancellation, messages, metadata, and media;
- interfaces for adapters, events, messages, tools, generation, persistence,
  realtime, and run state;
- type aliases for streams, schemas, tools, modalities, interrupts, and wire
  messages;
- variables and constants for event names, metadata, and capabilities.

## API lookup rules

1. Resolve the exact installed package and version first.
2. Prefer declarations from the installed artifact when they disagree with the
   hosted `latest` reference.
3. Use the immutable release source for `0.52.0` behavior.
4. Treat provider-adapter options as adapter APIs, not core APIs.
5. Do not infer a package version from a dependency's version.

## Missing or uneven API coverage

Many extension packages have task guides but no package-level API summary
matching the core and framework pages. This includes portions of persistence,
sandboxing, Code Mode, memory, MCP, devtools, isolates, and provider adapters.
For those packages, use their pinned README, changelog, exported declarations,
and focused guides.

The hosted `latest` reference may include symbols added after the `0.52.0`
release. A symbol present only on `latest` is not evidence that `0.52.0`
exports it.

## Sources

- https://tanstack.com/ai/latest/docs/migration/migration.md
- https://tanstack.com/ai/latest/docs/migration/migration-from-vercel-ai.md
- https://tanstack.com/ai/latest/docs/migration/ag-ui-compliance.md
- https://tanstack.com/ai/latest/docs/migration/sampling-options-to-model-options.md
- https://tanstack.com/ai/latest/docs/api/ai.md
- https://tanstack.com/ai/latest/docs/api/ai-client.md
- https://tanstack.com/ai/latest/docs/reference/index.md
- https://github.com/TanStack/ai/tree/b899fe5328f2907e5abbaa9c11b8f486caec229f/docs/reference
