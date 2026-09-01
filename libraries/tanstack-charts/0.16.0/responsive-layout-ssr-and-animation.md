---
library: "@tanstack/charts"
version: "0.16.0"
topic: "responsive layout, ssr, and animation"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/responsive-charts.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Responsive layout, SSR, and animation

The chart host resolves container dimensions, measures guides, compiles a scene, and renders it. Responsive definitions can derive a spec from resolved width and height. Server rendering and hydration require the server and client to agree on what can be measured and when. Animation operates on keyed scene updates.

## Implementation guidance

- Let the host own responsive dimensions unless the application has a deliberate fixed-size contract.
- Use responsive builders for layout decisions that truly depend on resolved surface size.
- Keep server output deterministic and defer browser-only measurement until the client host can observe it.
- Preserve stable mark keys across updates so animation connects the intended objects.

## Constraints and failure modes

- Reading browser dimensions during server rendering creates hydration differences.
- Animating data with changed identity produces exits and enters instead of a meaningful transition.
- A definition builder reads width and height but does not own or return the host size.
- Motion should respect reduced-motion preferences and must not hide a state change.

## Retrieval cues

Use this page when work mentions responsive layout, ssr, and animation, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/responsive-charts.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/ssr-and-hydration.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/dynamic-data-and-animation.md

