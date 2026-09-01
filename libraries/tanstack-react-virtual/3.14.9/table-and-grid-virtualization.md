---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "table and grid virtualization"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/table/README.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Table and grid virtualization

Virtual can window table rows, columns, or multi-lane grids while leaving semantic markup and sizing to the application. Row and column virtualizers may share one scroll element, but each axis needs its own count, estimate, positioning, and overscan policy.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Keep table data identity separate from the virtual index.
- Measure dynamic row height only on the row axis and use column sizes from the table model when available.
- Add spacer or transform offsets without breaking semantic row and cell relationships.
- Tune row and column overscan independently.

## Constraints and failure modes

- Invalid table markup can cause browser layout to override absolute positioning assumptions.
- Measuring both axes with one size value produces incorrect geometry.
- Firefox table-border measurement differences may require the documented measurement workaround.
- Virtualizing columns without accounting for padding offsets can misalign headers and cells.

## Retrieval cues

Use this page when work mentions table and grid virtualization, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/table/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/table/src/main.tsx
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md

