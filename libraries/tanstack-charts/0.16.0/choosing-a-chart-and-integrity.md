---
library: "@tanstack/charts"
version: "0.16.0"
topic: "choosing a chart and preserving integrity"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/choosing-a-chart.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Choosing a chart and preserving integrity

Chart choice begins with the comparison a reader must make. Bars support categorical magnitude, lines support ordered change, scatterplots support relationships, and areas encode magnitude or intervals relative to a baseline. Accessibility and large-data choices are part of correctness, not post-render decoration.

## Implementation guidance

- State the question and units in surrounding text, axes, or legends.
- Use a zero baseline for bars unless a clearly explained exception is essential.
- Provide keyboard focus and a table or textual summary when exact values matter.
- For dense data, track source, represented, prepared, and rendered counts separately.

## Constraints and failure modes

- Dual quantitative axes can imply a relationship between unrelated series.
- Three-dimensional effects distort position, length, and area.
- Rendering every observation is not automatically more honest when marks exceed available pixels.
- Color alone must not carry essential state, and missing or empty data must not look like zero.

## Retrieval cues

Use this page when work mentions choosing a chart and preserving integrity, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/choosing-a-chart.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/accessibility.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/large-data.md

