---
library: "@tanstack/ai"
version: "0.52.0"
topic: "persistence and resumable streams"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/persistence/overview.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# Persistence and resumable streams

Persistence records messages, generated artifacts, and run state so a client can restore a conversation. Resumable streams add a replay boundary and continuation protocol; they are not supplied by ordinary message storage alone. Custom adapters must preserve ordering, identifiers, and migration rules.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Persist stable thread, run, message, and chunk identifiers.
- Use the documented controls to decide which generated files and intermediate records survive.
- Make replay idempotent and resume from an acknowledged cursor or run boundary.
- Run storage migrations before interpreting older records with newer code.

## Constraints and failure modes

- Replaying already-applied tool or custom events can duplicate side effects.
- Dropping snapshots or terminal events can leave the restored client in a false running state.
- A WebSocket reconnect without durable replay can lose events.
- Changing an adapter schema without a migration can corrupt correlation among runs, messages, and artifacts.

## Retrieval cues

Use this page when work mentions persistence and resumable streams, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/persistence/overview.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/persistence/chat-persistence.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/persistence/controls.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/persistence/migrations.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/resumable-streams/overview.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/resumable-streams/websockets.md

