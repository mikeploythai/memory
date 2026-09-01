---
library: "@tanstack/ai"
version: "0.52.0"
topic: "structured outputs"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/structured-outputs/overview.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Structured outputs

Structured output constrains a model result with a supported schema and preserves the typed value in the run. TanStack AI documents one-shot generation, streaming partial JSON, multi-turn structured parts, and structured output combined with tools. The correct mode depends on whether the application needs one terminal object, visible progressive state, or an agent loop that may call tools before producing the object.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Use a supported Standard Schema implementation or JSON Schema and infer the result type from that schema.
- Treat streamed content as partial until the completion event validates the final object.
- Keep structured output attached to its turn when conversation history is replayed.
- When tools are enabled, define the stopping condition and distinguish tool events from the final structured result.

## Constraints and failure modes

- Never parse an arbitrary text response and label it schema-validated.
- Partial JSON can be syntactically incomplete; do not run irreversible work from an intermediate fragment.
- A schema that the provider cannot satisfy may end the run with validation failure rather than a usable object.
- Do not discard the terminal structured-output event when converting or persisting messages.

## Retrieval cues

Use this page when work mentions structured outputs, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/structured-outputs/overview.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/structured-outputs/one-shot.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/structured-outputs/streaming.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/structured-outputs/with-tools.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/structured-outputs/multi-turn.md

