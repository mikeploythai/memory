---
library: "@tanstack/ai"
version: "0.52.0"
topic: "agent memory"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/memory/overview.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Agent memory

TanStack AI memory is an adapter-driven subsystem for recalling relevant records and writing durable information around a run. The runtime defines the memory contract; storage and retrieval strategy remain application choices. The quickstart covers the default flow, while the operating and adapter guides define lifecycle and extension boundaries.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Resolve tenant and user scope before retrieval or writes.
- Bound recalled content by relevance and token budget, and record provenance when the UI must explain it.
- Use the documented adapter interface for custom storage instead of reaching into runtime internals.
- Keep transient conversation history distinct from durable memory records.

## Constraints and failure modes

- Do not place secrets or unrestricted private records into prompts merely because the memory backend returned them.
- Cross-tenant retrieval is a data isolation failure, not a ranking problem.
- Writing every message as durable memory creates duplication and low-quality recall.
- A custom adapter must preserve the runtime ordering and error behavior described by the contract.

## Retrieval cues

Use this page when work mentions agent memory, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/memory/overview.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/memory/quickstart.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/memory/operating.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/memory/adapters.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/memory/custom-adapter.md

