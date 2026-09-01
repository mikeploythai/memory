---
library: "@tanstack/charts"
version: "0.16.0"
topic: "migration, testing, and api boundaries"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/migrating.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Migration, testing, and API boundaries

Migration should first reproduce the existing chart semantics, interaction, and accessibility before removing the prior renderer. Tests can inspect definitions, scene output, focus behavior, and exported output. The API separates chart definitions, specs, adapters, rendering, interaction, and types so applications can extend one boundary without replacing the rest.

## Implementation guidance

- Inventory current data transforms, scale domains, axes, legends, interaction, export, and accessibility.
- Establish visual and behavioral parity with representative fixtures.
- Test empty, missing, dense, responsive, keyboard, and reduced-motion states.
- Use the exact 0.16.0 reference pages for definition and host signatures.

## Constraints and failure modes

- A screenshot alone does not verify data semantics, keyboard behavior, or selection state.
- Migrating chart type names without matching scale and transform behavior can silently alter meaning.
- Custom renderers and marks must honor stable scene keys and host contracts.
- Do not widen types or cast away host-specific tooltip compatibility.

## Retrieval cues

Use this page when work mentions migration, testing, and api boundaries, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/migrating.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/testing-and-debugging.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/typescript.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/reference/chart-definitions.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/reference/chart-spec.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/reference/rendering-and-export.md

