---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "measurement and scrolling pitfalls"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Measurement and scrolling pitfalls

Most Virtual defects come from inconsistent identity, coordinates, or sizing ownership. The virtualizer needs stable keys, one coherent measurement path per item, an accurate scroll element, and estimates that converge toward rendered sizes. Imperative scrolling uses those same measurements and may be corrected as sizes resolve.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Audit keys, `data-index`, surface size, transforms, scroll margin, and measurement callbacks together.
- Invalidate all measurements after a global width or typography change.
- Use `onChange` without expensive React state updates when direct DOM work is sufficient.
- Test append, prepend, resize, scroll-to-index, RTL, and reduced-motion cases.

## Constraints and failure modes

- Dynamic measurement plus smooth scrolling has no fixed target.
- Stale cached sizes create gaps, overlap, or wrong total size.
- Calling `scrollToIndex` repeatedly while measurement adjusts can oscillate.
- Direct DOM update mode requires the documented container ref and forbids application-owned item transforms.

## Retrieval cues

Use this page when work mentions measurement and scrolling pitfalls, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/framework/react/react-virtual.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/chat.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/pretext.md

