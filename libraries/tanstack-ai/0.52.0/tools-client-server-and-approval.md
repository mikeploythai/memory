---
library: "@tanstack/ai"
version: "0.52.0"
topic: "tools, execution location, and approval"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/tools.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Tools, execution location, and approval

A tool begins as a typed definition with a name, description, input schema, and optional output schema. Execution is attached separately. Server tools can access private services; client tools can perform browser-side work; provider tools are executed by the model provider. Approval is a first-class interruption, not a boolean prompt convention.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Share the tool definition when both sides need its types, but attach private execution only on the server.
- Validate model-produced input against the declared schema before executing side effects.
- Use approval metadata and the interrupt resolution flow for consequential operations.
- Return structured, serializable results and keep provider-executed tool metadata intact across turns.

## Constraints and failure modes

- A client tool cannot safely hold server credentials.
- Tool names must be unique in the active registry; duplicate names make dispatch ambiguous.
- Do not treat approval as granted because the model requested a tool.
- Do not re-execute provider tools locally when metadata identifies them as provider-executed.

## Retrieval cues

Use this page when work mentions tools, execution location, and approval, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/tools.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/server-tools.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/client-tools.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/tool-approval.md

