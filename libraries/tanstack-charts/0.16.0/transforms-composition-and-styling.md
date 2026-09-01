---
library: "@tanstack/charts"
version: "0.16.0"
topic: "transforms, composition, and styling"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/transforms-and-reactivity.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Transforms, composition, and styling

Transforms prepare rows for marks; faceting and composition combine views; legends and color explain encodings; themes inherit application styles through `currentColor` and chart CSS variables. These layers remain explicit so data work, visual encoding, and application state do not become a hidden series abstraction.

## Implementation guidance

- Memoize transformed data when its inputs are stable and the work is material.
- Use small multiples when aligned comparisons are clearer than overlapping scales.
- Choose categorical and quantitative color scales according to data meaning.
- Set chart theme variables at a container boundary and preserve contrast in both light and dark contexts.

## Constraints and failure modes

- Do not mutate source rows in a transform used elsewhere.
- Interior stack segments are hard to compare; use another composition when that comparison matters.
- A legend cannot repair an encoding with indistinguishable colors or missing units.
- Avoid global theme overrides that unintentionally change unrelated charts.

## Retrieval cues

Use this page when work mentions transforms, composition, and styling, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/transforms-and-reactivity.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/faceting-and-composition.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/legends-and-color.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/themes-and-styling.md

