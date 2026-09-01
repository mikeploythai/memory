---
library: "@tanstack/ai"
version: "0.52.0"
topic: "interrupts, persistence, and resumable streams"
source: "https://github.com/TanStack/ai/blob/b899fe5328f2907e5abbaa9c11b8f486caec229f/docs/interrupts/overview.md"
retrieved_at: "2026-08-31"
source_ref: "b899fe5328f2907e5abbaa9c11b8f486caec229f"
---

# Interrupts, persistence, and resumable streams

TanStack AI documents three related but separate concerns: pausing a run for
input, recording application state, and reconnecting to a stream. An
implementation may use one without using all three.

## Interrupts

Interrupts suspend progress until the application supplies a resolution. The
release documentation covers:

| Topic | Purpose |
|---|---|
| Overview | Core request/resolution model |
| Tool approval | Approval as a specialized interrupt |
| Multiple interrupts | Resolve more than one pending item |
| Generic interrupts | Define application-specific pauses |
| Lifecycle boundaries | Control where an interrupt may occur |
| Apply answers | Submit and validate resolutions |
| Migration | Move older approval flows to the interrupt model |

Treat correlation identifiers and resume payloads as protocol data. Preserve
them across serialization. Validate a resume batch before applying it, and
surface item-level errors rather than silently discarding invalid answers.

An approval request is not proof of approval. Execute the protected tool only
after the corresponding resolution authorizes it.

## Resumable streams

Resumable streams address transport interruption and continued delivery. The
guides cover an overview, advanced behavior, WebSockets, and custom durability
adapters.

Core reference areas include replaying a recorded run stream, requesting
cancellation, and resuming HTTP, SSE, or WebSocket delivery. A transport resume
must reconnect to the same logical run; starting a new `chat()` call is not a
substitute.

Durability and transport are separate choices. WebSockets change the delivery
channel, while a durability adapter determines what can be replayed after the
original process or connection is gone.

## Persistence

The persistence section covers:

- chat, client, and generation persistence;
- controls for persisted operations;
- custom persistence adapters;
- ID mapping between application and provider records;
- generated-file retention;
- store reference and persistence internals;
- persistence migrations.

The package versions are independent. For this release snapshot,
`@tanstack/ai-persistence` is `0.5.4`, while `@tanstack/ai` is `0.52.0`.
Never install `@tanstack/ai-persistence@0.52.0` by inference.

## Ownership model

| State | Expected owner |
|---|---|
| Provider request and streamed events | Core activity and adapter |
| Pending interrupt and its correlation | Run/interrupt layer |
| Durable event or message history | Configured run store or persistence adapter |
| Browser presentation state | Headless client or framework binding |
| Replay cursor and reconnect transport | Resumable-stream layer |

Keep provider secrets and trusted tool execution outside browser-persisted
state. Persist only the content and metadata the application is authorized to
retain.

## Failure modes

- Resuming with a different run identifier.
- Replaying a tool call that already completed before disconnection.
- Marking an interrupted or aborted drive as completed.
- Persisting provider metadata but dropping the correlation needed to resume.
- Applying only part of a batch without reporting rejected resolutions.
- Assuming an in-memory run store survives a process restart.
- Treating generated artifacts as ordinary message text.

## Migration boundaries

Keep interrupt migration and persistence-store migration as separate tasks.
The former changes request/resolution protocol behavior; the latter may change
stored schemas, IDs, or adapter contracts. Test replay against records written
by the source version before changing production storage.

## Coverage limits

This page does not reproduce a complete store implementation, schema migration,
or WebSocket server. Those are implementation-sensitive and must be retrieved
from the pinned package guide and API reference selected for the application's
transport and adapter.

## Sources

- https://tanstack.com/ai/latest/docs/interrupts/overview.md
- https://tanstack.com/ai/latest/docs/interrupts/multiple.md
- https://tanstack.com/ai/latest/docs/interrupts/apply-answers.md
- https://tanstack.com/ai/latest/docs/interrupts/migration.md
- https://tanstack.com/ai/latest/docs/resumable-streams/overview.md
- https://tanstack.com/ai/latest/docs/resumable-streams/websockets.md
- https://tanstack.com/ai/latest/docs/resumable-streams/custom-adapter.md
- https://tanstack.com/ai/latest/docs/persistence/overview.md
- https://tanstack.com/ai/latest/docs/persistence/migrations.md
- https://tanstack.com/ai/latest/docs/persistence/store-reference.md
