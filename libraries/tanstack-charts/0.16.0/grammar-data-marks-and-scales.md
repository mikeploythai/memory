---
library: "@tanstack/charts"
version: "0.16.0"
topic: "grammar, data, marks, and scales"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/concepts/grammar-of-graphics.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Grammar, data, marks, and scales

TanStack Charts uses a grammar of graphics: each mark receives its own data, channels map fields or accessors to visual properties, scales map domains to ranges, and ordered marks form layers. Chart definitions compile this declarative input into a responsive keyed scene. Data preparation remains outside the runtime unless an explicit transform is imported.

## Implementation guidance

- Choose a mark based on the analytical question and bind only the channels it needs.
- Use stable keys when identity cannot be inferred from IDs or unique positions.
- Start with compact TanStack scales; import specialized D3 behavior only where needed.
- Prepare, clean, aggregate, and sort data explicitly before passing it to marks.

## Constraints and failure modes

- Connecting unordered categories with a line implies continuity that is not present.
- Unstable or duplicate keys break update and selection continuity.
- Implicitly mixing incompatible scale domains across layers can produce misleading alignment.
- The chart runtime does not fetch, clean, or automatically choose an honest representation.

## Retrieval cues

Use this page when work mentions grammar, data, marks, and scales, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/concepts/grammar-of-graphics.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/concepts/data-and-channels.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/concepts/marks-and-layering.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/concepts/scales-and-d3.md

