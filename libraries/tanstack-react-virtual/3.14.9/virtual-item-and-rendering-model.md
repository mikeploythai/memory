---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "virtual item and rendering model"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/introduction.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Virtual item and rendering model

A virtual item describes one rendered index with a key, start offset, end offset, size, and lane. The virtualizer calculates a visible range plus overscan; the application positions those items within a full-size scroll surface. Only the visible DOM is small—the logical scroll range still represents every item.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Use `virtualItem.key` for rendered identity.
- Position items from `virtualItem.start`, adjusted for documented scroll margin when applicable.
- Treat `size` as measured or estimated state owned by the virtualizer.
- Choose overscan as a latency-versus-DOM tradeoff rather than a fixed rule.

## Constraints and failure modes

- Mapping the full dataset instead of virtual items removes the performance benefit.
- Ignoring start offsets stacks visible items at the same origin.
- Subtracting the wrong scroll margin shifts content and breaks scroll-to alignment.
- Large overscan can recreate the DOM cost virtualization was meant to avoid.

## Retrieval cues

Use this page when work mentions virtual item and rendering model, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/introduction.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtual-item.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md

