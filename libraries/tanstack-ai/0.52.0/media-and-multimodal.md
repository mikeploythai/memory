---
library: "@tanstack/ai"
version: "0.52.0"
topic: "media and multimodal generation"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/multimodal-content.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Media and multimodal generation

TanStack AI models images, video, audio, speech, transcription, and realtime sessions as separate typed activities. Multimodal chat parts carry URLs or data with metadata; generation hooks follow an activity lifecycle rather than pretending every output is text. Provider and model capability types constrain the available inputs and options.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Resolve the exact provider model and its supported modalities before constructing input.
- Keep large media out of message JSON when an authenticated URL or application storage reference is appropriate.
- Handle asynchronous video jobs and cancellation as long-running work.
- Validate MIME type, size, duration, and source before relaying user media to a provider.

## Constraints and failure modes

- A text-only model cannot accept image or audio parts even if the transport can serialize them.
- Base64 media can exceed route, memory, or provider limits quickly.
- Do not expose provider API keys in browser recording or realtime setup; mint scoped tokens when the adapter supports them.
- Generated media may be delayed or rejected; a request acknowledgement is not a completed artifact.

## Retrieval cues

Use this page when work mentions media and multimodal generation, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/advanced/multimodal-content.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/media/generations.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/media/image-generation.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/media/video-generation.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/media/transcription.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/media/realtime-chat.md

