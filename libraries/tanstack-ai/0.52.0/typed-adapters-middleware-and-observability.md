---
library: "@tanstack/ai"
version: "0.52.0"
topic: "typed adapters, middleware, and observability"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/typed-options.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Typed adapters, middleware, and observability

Provider adapters expose model-specific capabilities and option types. Middleware wraps generation without erasing those contracts, while debug logging and OpenTelemetry observe activity and usage. Runtime adapter switching is supported, but the intersection of capabilities is not automatically the same for every selected model.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Keep model selection narrow enough for TypeScript to infer its real options.
- Use middleware for cross-cutting behavior such as logging or policy, and preserve abort and error propagation.
- Redact prompts, tool inputs, credentials, and provider payloads before logging.
- Record model, provider, run, finish reason, latency, and usage with stable correlation IDs.

## Constraints and failure modes

- Casting provider options to a broad record removes the compile-time checks the adapter supplies.
- Middleware that consumes or rewrites a stream incorrectly can drop terminal, usage, or tool events.
- Debug logs may contain user content and secrets.
- Switching adapters at runtime can invalidate modalities, tools, structured-output support, or option names.

## Retrieval cues

Use this page when work mentions typed adapters, middleware, and observability, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/typed-options.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/per-model-type-safety.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/runtime-adapter-switching.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/middleware.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/debug-logging.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/otel.md

