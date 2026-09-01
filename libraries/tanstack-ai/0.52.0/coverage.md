---
library: "@tanstack/ai"
version: "0.52.0"
topic: "documentation coverage"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/config.json"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# TanStack AI documentation coverage

This map records what the 2026-08-31 indexing batch covers and, just as importantly, where it stops. The exact release ref is the authority. Hosted `latest` pages are moving references and are not used to silently extend this version.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Indexed in this batch

- React and server streaming chat
- Tools, approvals, structured outputs, interrupts, memory, MCP, and Code Mode
- Persistence, resumable streams, multimodal activities, typed adapters, middleware, observability, and migrations
- Grouped core/client/React API entry points

## Deferred

- Individual provider-adapter pages
- Sandbox provider, durability, snapshots, artifacts, and policy subtopics
- Embeddings, reranking, skills, community adapters, and every media provider
- Hundreds of generated class, function, interface, type-alias, and variable pages
- Framework quick starts other than React and React Native

## Not present in the exact-version documentation

- A repository `llms.txt` at this ref
- One official anti-patterns page; failure modes are distributed through guides
- A single provider package version shared by all adapters

## Stopping point

This batch stops at the prioritized implementation paths above. Deferred material should be added only when a task needs it, using the same immutable ref and one retrieval-oriented page per coherent topic. Generated symbol references remain discoverable through the official index; they are grouped here rather than copied one file per symbol.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/config.json
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/getting-started/overview.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/reference/index.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/packages/ai-react/CHANGELOG.md

