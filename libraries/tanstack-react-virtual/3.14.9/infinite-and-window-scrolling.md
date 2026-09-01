---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "infinite and window scrolling"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/infinite-scroll/README.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Infinite and window scrolling

Infinite scrolling combines a virtual range with data loading near an edge. Window virtualization uses the document window rather than a nested element and must account for the list surface position. Loading policy stays outside Virtual; the virtualizer reports ranges and offsets.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Reserve a loader row or trigger fetching from the reported range before the user reaches the end.
- Deduplicate in-flight page requests and update count only when data state changes.
- For window scrolling, calculate the list scroll margin from its document position.
- Preserve item keys as pages append or prepend.

## Constraints and failure modes

- Repeated `onChange` calls can launch duplicate fetches without an in-flight guard.
- A count that includes unloaded items without a render plan creates blank ranges.
- Window offsets are wrong when the list position is ignored.
- Prepending data with index keys can move cached sizes to different records.

## Retrieval cues

Use this page when work mentions infinite and window scrolling, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/infinite-scroll/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/window/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md

