---
library: "@tanstack/ai"
version: "0.52.0"
topic: "interrupts and human approval"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/interrupts/overview.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Interrupts and human approval

Interrupts suspend an agent run at a defined boundary and expose typed resolution data to the client. Tool approval is one specialization; generic interrupts can ask for missing information or a decision. Multiple pending interrupts require correlation so answers resume the intended run and item.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Define the interrupt schema and resolution shape instead of passing untyped arbitrary payloads.
- Persist run, thread, and interrupt correlation identifiers together.
- Validate a batch of resolutions before resuming any part of it.
- Show whether an interrupt was restored from persistence or arrived live when that distinction affects cancellation.

## Constraints and failure modes

- Applying an answer to the wrong run or tool call can resume unrelated work.
- A cancelled, expired, or already-resolved interrupt must not be applied again.
- Client-side display is not an authorization boundary; server-side policy still decides whether execution may continue.
- Migration from older approval handling requires preserving correlation and snapshot semantics.

## Retrieval cues

Use this page when work mentions interrupts and human approval, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/interrupts/overview.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/interrupts/boundaries.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/interrupts/tool-approval.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/interrupts/apply-answers.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/interrupts/multiple.md

