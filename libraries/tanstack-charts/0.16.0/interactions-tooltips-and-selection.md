---
library: "@tanstack/charts"
version: "0.16.0"
topic: "interactions, tooltips, and selection"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/interactions-and-selections.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Interactions, tooltips, and selection

Charts owns datum focus, keyboard navigation, crosshairs, selection callbacks, and optional controls. The application owns accepted semantic values, shared controller identity, and product policy. Tooltips attach presentation to focused data but should not become the only access path to information.

## Implementation guidance

- Use native focus for nearest-point inspection, grouped axis tooltips, snapped crosshairs, and keyboard navigation.
- Use controlled chart controls when selection or cursor state must be shared or persisted.
- Keep controller and definition identity stable across renders.
- Expose the same essential values through focus, pointer, and accessible text.

## Constraints and failure modes

- Do not make hover the only way to read a value.
- Recreating a controlled selection object can discard continuity or trigger redundant updates.
- The chart does not own application authorization or filtering policy.
- Tooltip portals and host-specific definitions must match the rendering platform.

## Retrieval cues

Use this page when work mentions interactions, tooltips, and selection, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/interactions-and-selections.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/guides/tooltips-and-focus.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/reference/focus-and-interaction.md

