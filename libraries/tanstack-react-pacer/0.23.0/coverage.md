---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "coverage map"
source: "https://tanstack.com/pacer/latest/llms.txt"
retrieved_at: "2026-09-07"
source_ref: "c75895520669b08dc8946b42e1a6d529ca977230"
---

# TanStack React Pacer 0.23.0 coverage map

This adapter-specific map complements `@tanstack/pacer@0.22.0`. The adapter
and core versions differ and must remain separate.

## First-party indices and refs inspected

| Source | Result |
|---|---|
| https://tanstack.com/pacer/latest/llms.txt | Moving index used to inventory React adapter guides and references |
| https://github.com/TanStack/pacer/tree/c75895520669b08dc8946b42e1a6d529ca977230/docs/framework/react | Immutable React documentation tree |

## Bootstrap chain

| Requirement | Status | Evidence or gap |
|---|---|---|
| Package choice and prerequisites | partial | The [core package-choice page](../../tanstack-pacer/0.22.0/package-choice-installation-and-quick-start.md) pairs React adapter `0.23.0` with core `0.22.0`; runtime/tooling ranges are absent |
| Project creation | not applicable | Pacer assumes an existing React application |
| Installation | partial | The React package and npm command are indexed in the core package-choice page, but the command is unpinned |
| Required files, provider, and configuration | partial | Adapter APIs and provider routing are known, but no complete provider or entry-file setup is retained |
| Getting started and mental model | partial | Core timing-policy guidance is indexed; a canonical React debounce/throttle quick start is not retained |
| Minimal runnable application | partial | Queue and batch components are present but depend on application-owned functions and a host app |
| Run/build verification | blocked | No project scripts, timing test, or production-build verification is indexed |
| Setup mistakes and version caveats | partial | Core/adapter version separation, policy selection, retry risks, and persistence limits are covered |

Greenfield setup is blocked. The current React adapter corpus supports bounded
queue and batch work but not a complete first-project path or verified common
debounce flow.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Greenfield React application | blocked | Host creation, entry files, and build verification are missing |
| Add React queue or async queue | partial | [Queues, batches, async retry, and persistence](queues-batches-async-retry-and-persistence.md); application actions and verification are external |
| Add canonical React debounce, throttle, or rate limit | blocked | Core concepts exist, but exact React hook examples are not retained |
| Add batching, retry, or persistence | partial | Selected adapter examples and decision points are indexed; exact trigger, retry, and persistence contracts remain deferred |
| Debug timing/state behavior | partial | Failure risks are recorded; no dedicated troubleshooting workflow exists |
| Migration | blocked | No migration guide; breaking changes remain in changelogs |
| Production/build concerns | partial | Retry/idempotency and browser-persistence boundaries are covered; host build is unverified |

## Source coverage

| Source area | Status | Memory page or gap |
|---|---|---|
| Installation, package choice, and utility selection | indexed | Core [package choice and quick start](../../tanstack-pacer/0.22.0/package-choice-installation-and-quick-start.md) |
| React queues, batches, async retry, and persistence | indexed, bounded | [Queues, batches, async retry, and persistence](queues-batches-async-retry-and-persistence.md) |
| React debounce, throttle, and rate-limit guides | deferred | Present upstream; no substantive adapter page in this batch |
| React adapter and provider setup | deferred | API routing is known; executable configuration is not retained |
| Generated hook and option references | deferred | Exact signatures require pinned generated reference pages |
| Migration and troubleshooting | not present | No dedicated first-party sections found |

## Patterns, warnings, and stopping point

The indexed material distinguishes retained queues from discard-oriented
timing utilities, records concurrency and batching intent, and warns about
retry idempotency and browser-only persistence. This audit adds the missing
adapter coverage map only.

## Sources

- https://github.com/TanStack/pacer/tree/c75895520669b08dc8946b42e1a6d529ca977230/docs/framework/react

