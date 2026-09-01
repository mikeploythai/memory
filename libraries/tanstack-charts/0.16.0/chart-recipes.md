---
library: "@tanstack/charts"
version: "0.16.0"
topic: "chart recipes"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/examples/bars-and-rankings.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Chart recipes

The official examples organize compositions by analytical form rather than by a single monolithic chart component. Bars and rankings compare categories, lines and areas show ordered change or intervals, scatterplots show relationships, distributions summarize shape, and interactive examples add focus or selection without changing the underlying grammar.

## Implementation guidance

- Start from the closest analytical recipe, then replace its data and labels before adding layers.
- Keep data local to the mark when different layers use different prepared rows.
- Use an explicit temporal scale for time and an area-preserving radius for bubbles.
- Verify ordering, aggregation, missing values, focus, and smallest supported container.

## Constraints and failure modes

- Do not select a recipe because its appearance is fashionable; preserve the comparison it was designed to make.
- Area fills imply magnitude or interval, not merely emphasis.
- A dense scatterplot may need aggregation, binning, or density representation.
- Interactive decoration must not change the data semantics or hide keyboard behavior.

## Retrieval cues

Use this page when work mentions chart recipes, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/examples/bars-and-rankings.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/examples/lines-and-areas.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/examples/scatterplots-and-relationships.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/examples/distributions.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/examples/interactive-charts.md

