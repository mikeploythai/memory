---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "documentation coverage map"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/overview.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# TanStack React Form documentation coverage

This batch indexes the React v1 material most likely to affect implementation correctness. The hosted `llms.txt` is the complete moving index. Commit `b865ef335a69aa08a2f160895258f13e03773467` is the verified release boundary where `packages/react-form/package.json` is version 1.33.5.

## Indexed in this batch

- Quick start, concepts, defaults, deep-path typing, fields, forms, and selected subscriptions.
- Functional and Standard Schema validation, custom and field-level errors, dynamic/async validation, listeners, and linked fields.
- Async initial values, TanStack Query coordination, arrays, groups, reusable form composition, large forms, and multi-step workflows.
- Submission, schema transforms, server errors, Start/Next/Remix integration, UI-library wiring, focus management, React Native, debugging, devtools, and API routing.

## Deferred but present upstream

- Philosophy and comparison pages, which explain project positioning rather than implementation contracts.
- Individual generated core and React symbol pages. The API map links to them; copy one only when an exact signature is needed.
- Complete runnable source for simple, compiler, Expo, UI-library, server-action, Query, dynamic-validation, and composition examples. High-value examples are linked from topic pages.
- Non-React adapters and their framework-specific guides.
- Meta-framework adapter package references beyond the shared integration workflow.

## Not present as dedicated upstream sections

There is no single anti-patterns page. The source distributes failure modes across validation, composition, SSR, reactivity, and debugging guides; this batch retains them with the relevant topic. Accessibility is discussed through headless UI and focus patterns, but there is no exhaustive accessibility specification for every component library.

## Stopping point

The batch stops at ten topic pages plus this map. It does not mirror generated references or every example. Future work should route through `llms.txt`, prefer the exact release-commit file, and add only the smallest topic needed for a concrete implementation or debugging task.

## Sources

- [Official Form llms.txt](https://tanstack.com/form/latest/llms.txt)
- [Immutable documentation tree](https://github.com/TanStack/form/tree/b865ef335a69aa08a2f160895258f13e03773467/docs)
- [Pinned React package manifest](https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/packages/react-form/package.json)

