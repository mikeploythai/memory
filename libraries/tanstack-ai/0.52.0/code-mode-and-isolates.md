---
library: "@tanstack/ai"
version: "0.52.0"
topic: "code mode and isolates"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/code-mode/code-mode.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Code mode and isolates

Code Mode lets a model produce TypeScript that orchestrates a constrained tool surface. An isolate driver executes that code outside the application process, while the client receives execution and tool events. Snippets and lazy tools reduce repeated code and catalog overhead. The sandbox or isolate remains an application-owned security boundary.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Expose a narrow, typed tool API and deny ambient access not required by the task.
- Apply time, memory, output, network, and file limits in the isolate provider.
- Stream execution events to the client without exposing secret environment values.
- Validate snippet identity and version before allowing generated code to call it.

## Constraints and failure modes

- Generated code is untrusted even when it type-checks.
- Running Code Mode in the web server process defeats isolation and can leak credentials or corrupt state.
- An unrestricted package loader or network client can bypass the intended tool policy.
- Do not assume killing the client connection stops durable sandbox work; cancellation must reach the run.

## Retrieval cues

Use this page when work mentions code mode and isolates, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/code-mode/code-mode.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/code-mode/client-integration.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/code-mode/code-mode-isolates.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/code-mode/lazy-tools.md

