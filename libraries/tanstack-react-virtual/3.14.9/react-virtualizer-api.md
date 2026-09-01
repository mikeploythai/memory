---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "react virtualizer api"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/framework/react/react-virtual.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# React virtualizer API

The React adapter supplies `useVirtualizer` for element scrolling and `useWindowVirtualizer` for window scrolling, preconfiguring observation and scrolling functions around the core `Virtualizer`. The application still owns the scroll container, item markup, positioning styles, and the source data.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Provide `count`, a stable `getScrollElement`, and a realistic `estimateSize`.
- Render only `getVirtualItems()` and size the inner surface with `getTotalSize()`.
- Use `data-index` when attaching the default `measureElement` callback.
- Memoize item keys and callbacks whose identity affects measurement or updates.

## Constraints and failure modes

- A missing overflow container or inner total-size surface prevents correct scrolling.
- Using array indices as keys for reordered/prepended data can attach measurements to the wrong item.
- React-specific `useFlushSync` and direct DOM update modes have documented tradeoffs and structural requirements.
- Do not treat the adapter as a list component; layout remains application-owned.

## Retrieval cues

Use this page when work mentions react virtualizer api, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/framework/react/react-virtual.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md

