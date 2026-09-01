---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "scroll padding, margin, and custom scrolling"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/padding/README.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Scroll padding, margin, and custom scrolling

Padding changes the logical content edges; scroll padding changes where imperative scrolling aligns an item; scroll margin accounts for the virtual surface offset inside its scroll element. A custom `scrollToFn` can implement animation or platform behavior and receives adjustment information from measurement corrections.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Use the option that matches the intended coordinate: content padding, alignment padding, or surface margin.
- Subtract scroll margin when translating virtual starts into local element transforms.
- Delegate final offset writes to the documented element or window scroll helper.
- Cancel an older custom animation when a newer scroll request arrives.

## Constraints and failure modes

- Smooth scrolling is incompatible with ongoing dynamic measurement because the target changes during animation.
- Confusing padding with scroll padding produces unexpected start/end alignment.
- Ignoring measurement adjustments makes custom scroll destinations drift.
- Multiple active animation loops fight over scroll position.

## Retrieval cues

Use this page when work mentions scroll padding, margin, and custom scrolling, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/padding/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/scroll-padding/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/smooth-scroll/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/api/virtualizer.md

