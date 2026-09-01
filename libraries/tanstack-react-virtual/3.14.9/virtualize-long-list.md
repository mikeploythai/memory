---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "fixed, variable, and dynamic lists"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/fixed/README.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Fixed, variable, and dynamic lists

Fixed lists use one dependable estimate; variable lists compute estimates from item knowledge; dynamic lists attach measurement to rendered elements. Estimates establish the initial scroll geometry, and measurements correct it as real content appears.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Use a high, realistic estimate for dynamically measured items to reduce backward scroll adjustment.
- Attach `measureElement` to each dynamic row and keep its `data-index` accurate.
- Call `measure()` when a global layout input such as width or font changes.
- Use `resizeItem` when the application knows a final size without DOM measurement.

## Constraints and failure modes

- Do not use `measureElement` and `resizeItem` as competing owners for the same item without a deliberate override.
- Poor estimates cause visible correction and inaccurate initial scroll-to behavior.
- Measuring hidden or incorrectly styled elements records unusable sizes.
- Changing content without notifying or remeasuring leaves cached offsets stale.

## Retrieval cues

Use this page when work mentions fixed, variable, and dynamic lists, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/fixed/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/variable/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/dynamic/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md

