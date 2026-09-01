---
library: "@tanstack/ai"
version: "0.52.0"
topic: "coverage map"
source: "https://tanstack.com/ai/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "b899fe5328f2907e5abbaa9c11b8f486caec229f"
---

# TanStack AI 0.52.0 coverage map

This bounded draft covers the core product model, a partial React/server
bootstrap, chat and structured output, durable workflows, migrations, and API
routing. It does not claim complete coverage of all 64 public packages.

## First-party indices and refs inspected

| Source | Result |
|---|---|
| https://tanstack.com/ai/latest/llms.txt | Moving machine-readable index; sections are Get Started, Guides, and API |
| https://tanstack.com/ai/latest/docs/index.md | Markdown docs index equivalent |
| https://github.com/TanStack/ai/releases/tag/%40tanstack/ai%400.52.0 | Core release record |
| https://github.com/TanStack/ai/tree/b899fe5328f2907e5abbaa9c11b8f486caec229f | Immutable release source used for pinning |
| Release `docs/` tree | 630 Markdown files, including 460 generated reference pages |
| Package manifests plus npm `latest` | 64 public package versions checked; no differences found |

No `llms-full.txt` endpoint was present.

## Bootstrap chain

| Requirement | Evidence in this batch | Status |
|---|---|---|
| Package choice and prerequisites | [`bootstrap-react-and-server.md`](bootstrap-react-and-server.md) identifies core, client, React, and provider roles | partial |
| Installation or project creation | Verified `npm i` package commands are present | partial |
| Required files, providers, and configuration | Server/client boundary described; exact quick-start filenames and credential variable not retained | blocked |
| Getting started and core mental model | Core `chat()` shape and package split are present | partial |
| Manual setup/build from scratch | No standalone first-party manual-setup page found | not applicable |
| Minimal runnable application | Core call is executable in shape, but no complete server route plus React component is retained | blocked |
| Verification/build command | Exact dev/build script and expected browser/server result were not verified | blocked |
| Setup mistakes and version caveats | Independent package versions and moving-doc mismatch recorded | ready |

Greenfield setup is not ready because required files and verification evidence
remain blocked.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Greenfield setup | blocked | Bootstrap chain lacks a complete pinned application and run check |
| Common chat/tool/structured-output feature work | partial | [`chat-streaming-tools-and-structured-output.md`](chat-streaming-tools-and-structured-output.md) |
| Debugging | partial | Failure modes are mapped, but no dedicated troubleshooting corpus or full event signatures are indexed |
| Migration | partial | [`migrations-and-api-map.md`](migrations-and-api-map.md) routes guides but does not retain source-version pages |
| Production/build concerns | partial | Persistence and durability are mapped; deployment, security, and build verification remain deferred |

## Substantive source-section mapping

| Source section | Status | Indexed page or reason |
|---|---|---|
| Getting started | partial | [`bootstrap-react-and-server.md`](bootstrap-react-and-server.md); framework variants deferred |
| Chat and streaming | indexed | [`chat-streaming-tools-and-structured-output.md`](chat-streaming-tools-and-structured-output.md) |
| Structured outputs | indexed at overview level | Same page; symbol-level interfaces deferred |
| Tools and MCP | indexed at overview level | Same page; MCP codegen and manual clients deferred |
| Middleware and observability | deferred | Separate advanced batch needed |
| Interrupts | indexed at overview level | [`interrupts-persistence-and-resumable-streams.md`](interrupts-persistence-and-resumable-streams.md) |
| Resumable streams | indexed at overview level | Same page; complete transport implementations deferred |
| Persistence | indexed at overview level | Same page; adapter/store implementations deferred |
| Media generation and realtime | deferred | Separate activity/adapters batch needed |
| Embeddings and reranking | deferred | Separate activity/adapters batch needed |
| Code Mode | deferred | Independent packages and isolate drivers need exact version pages |
| Sandbox and durable runs | deferred | Large section with provider-specific packages |
| Memory | deferred | `@tanstack/ai-memory@0.1.9` needs its own package page |
| Agent skills | deferred | `@tanstack/ai-skills@0.1.1` needs its own package page |
| Provider adapters | deferred | Each adapter is independently versioned |
| Community adapters | not applicable | Not first-party package authority for this bounded core batch |
| Migrations | indexed as route map | [`migrations-and-api-map.md`](migrations-and-api-map.md) |
| Package API pages | indexed as route map | Same page |
| Generated reference | partial | Area and lookup rules indexed; 460 symbol pages not copied |

## Recipes, patterns, and warnings

| Category | Coverage |
|---|---|
| Recipes | Core `chat()` construction and package selection retained |
| Reusable patterns | Trusted server/client split, typed streams, tool ownership, durable resume boundaries |
| Warnings | Do not infer versions; do not expose provider secrets; do not replay completed tools |
| Anti-patterns | Root-level sampling options, plain-text treatment of event streams, provider-tool re-execution |
| Troubleshooting | No dedicated top-level troubleshooting section found; only failure-mode routing retained |
| Migrations | Six migration areas identified; full source/target pairs not retained |
| API | Core/framework summaries and generated-reference areas mapped |

## Version and package mismatches

- Hosted `latest` followed post-release `main`, not the immutable `0.52.0`
  commit.
- The release contains Vue, Svelte, Angular, and Octane quick starts that the
  current hosted index no longer lists.
- Companion packages have independent versions. Examples include
  `@tanstack/ai-client@0.29.2`, `@tanstack/ai-react@0.22.4`, and
  `@tanstack/ai-persistence@0.5.4`.
- Extension guides do not consistently have package-level API summaries.

## Meaningful gaps

- No `llms-full.txt`.
- No standalone installation/prerequisites or first-build page.
- No dedicated top-level troubleshooting guide.
- No complete executable application and verification command in this batch.
- No per-package pages for adapters, media, persistence, sandbox, Code Mode,
  memory, skills, or devtools.

## Bounded stopping point

This batch stops after five `@tanstack/ai@0.52.0` pages. The next batch should
first complete one immutable React/server bootstrap and its build verification,
then create exact-version pages for whichever companion packages that example
uses. Do not mark greenfield setup ready before that work succeeds.

## Sources

- https://tanstack.com/ai/latest/llms.txt
- https://github.com/TanStack/ai/tree/b899fe5328f2907e5abbaa9c11b8f486caec229f/docs
- https://github.com/TanStack/ai/tree/b899fe5328f2907e5abbaa9c11b8f486caec229f/packages
