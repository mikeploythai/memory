---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "sticky items and range extraction"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/sticky/README.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Sticky items and range extraction

Sticky headers require rendering an item that may fall outside the ordinary visible range. A custom `rangeExtractor` starts from the default range and adds the active sticky index. The application then applies sticky positioning or layering while the virtualizer continues to own range and measurement math.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Compose with the default range extractor rather than rebuilding overscan behavior.
- Return unique, sorted indexes that remain within the current count.
- Find the active sticky item from stable application data and visible range.
- Give sticky content the required positioning and stacking context.

## Constraints and failure modes

- Replacing the default range entirely can omit ordinary visible items or overscan.
- Duplicate or out-of-range indexes lead to unstable rendering.
- A sticky element with different measured height can shift later offsets if sizing is not consistent.
- CSS sticky behavior still depends on the correct scroll container and overflow ancestors.

## Retrieval cues

Use this page when work mentions sticky items and range extraction, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/sticky/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/sticky/src/main.tsx
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md

