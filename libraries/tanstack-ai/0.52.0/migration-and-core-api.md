---
library: "@tanstack/ai"
version: "0.52.0"
topic: "migration and core api"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/migration/migration.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Migration and core API

The 0.52.0 documentation includes migration material for the unified chat architecture, Vercel AI SDK users, sampling-to-model option changes, and AG-UI compliance. The generated API pages enumerate the exact core, client, and React exports. Migration should preserve behavior and protocol state before removing the old integration.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Inventory current message shapes, stream protocol, tool execution location, persistence, and provider options before changing imports.
- Migrate transport and message conversion together so the client and server agree on AG-UI events.
- Replace provider-neutral sampling fields with the documented model option path.
- Use the exact generated API pages to confirm signatures and renamed exports.

## Constraints and failure modes

- Do not mix old proprietary stream parsing with AG-UI response helpers.
- A source-compatible type change can still alter persisted wire data or tool-loop behavior.
- Vercel AI SDK abstractions do not map one-to-one; confirm tools, structured output, and client persistence separately.
- Avoid copying signatures from hosted `latest` into a 0.52.0 implementation.

## Retrieval cues

Use this page when work mentions migration and core api, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/migration/migration.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/migration/migration-from-vercel-ai.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/migration/sampling-options-to-model-options.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/migration/ag-ui-compliance.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/api/ai.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/api/ai-react.md

