---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "chat end anchoring"
source: "https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/chat.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9"
---

# Chat end anchoring

Chat timelines grow at both ends and their rows resize while content streams. End anchoring keeps the latest edge stable, append following can keep a reader pinned only when appropriate, and history prepends must compensate scroll position so the visible message does not jump.

## Version boundary

The React adapter is `@tanstack/react-virtual` 3.14.9. Its exact changelog records `@tanstack/virtual-core` 3.17.7. Core option and instance behavior belongs to that companion version.

## Implementation guidance

- Use stable message IDs as item keys.
- Choose end anchoring for initial and resizing behavior, then define append-follow policy separately.
- Measure message bubbles as text or media changes.
- Guard history loading and preserve the visible anchor while prepending.

## Constraints and failure modes

- Do not force-scroll to the end when the reader has intentionally moved upward.
- Prepending with index keys remaps every cached measurement.
- Images, markdown, and streamed text can change height after the first measure.
- An initial scroll command issued before the scroll element and measurements exist may be clamped or corrected later.

## Retrieval cues

Use this page when work mentions chat end anchoring, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/docs/chat.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/chat/README.md
- https://github.com/TanStack/virtual/blob/%40tanstack%2Freact-virtual%403.14.9/examples/react/chat/src/main.tsx

