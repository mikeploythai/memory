---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "pretext text measurement"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/pretext.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Pretext text measurement

Pretext can estimate wrapped text height before DOM measurement. Cache text preparation by content and typography inputs, then run width-dependent layout for the current container. Virtual still owns range, positioning, and scrolling; Pretext supplies an estimate for rows dominated by text.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Match canvas font, line height, letter spacing, white-space, and word-break to rendered CSS.
- Rerun layout on width changes and clear caches after fonts become ready.
- Clamp empty text when the rendered UI reserves one line.
- Use DOM measurement or `resizeItem` for images, embeds, block layout, or content whose height is not text-derived.

## Constraints and failure modes

- System font aliases can resolve differently between CSS and canvas.
- Pretext requires Canvas 2D measurement and `Intl.Segmenter`; keep a fallback.
- Do not prepare text again for every resize when only layout width changed.
- Using both Pretext sizing and DOM measurement without an ownership rule causes correction churn.

## Retrieval cues

Use this page when work mentions pretext text measurement, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/pretext.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/pretext/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/pretext/src/main.tsx

