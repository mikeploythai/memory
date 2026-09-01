---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "documentation coverage map"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/overview.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# TanStack React Hotkeys documentation coverage

This batch indexes the complete conceptual React guide set plus routing to generated APIs and examples. The official `llms.txt` is the moving full index. Commit `c73a3a167c979d500e1008341ecad096a6c4e635` is the release boundary for `@tanstack/react-hotkeys` 0.10.0; its core dependency is `@tanstack/hotkeys` 0.8.0.

## Indexed in this batch

- Registration, plural hooks, provider defaults, event propagation, input filtering, conflicts, metadata, lifecycle cleanup, and dynamic lists.
- Sequences, timeouts, modifiers, overlap, chord and sequence recording, commit/cancel behavior, and canonical custom bindings.
- Held logical keys, physical codes, hold duration, blur cleanup, platform formatting, parsing, normalization, validation, React recipes, devtools, and API routing.

## Deferred but present upstream

- Individual generated core and React symbol pages. The API map groups and links them; copy one only when an exact signature is needed.
- Full source for each React example. The recipes page links the main examples.
- Angular, Lit, Preact, Solid, Svelte, Vue, and vanilla adapters, guides, references, and examples.
- Devtools adapter implementation details beyond setup and diagnostic use.

## Not present as dedicated upstream sections

There is no standalone accessibility guide or anti-patterns page. Input safety, focus implications, propagation, conflicts, platform behavior, and recorder interaction constraints are distributed through the six React guides and have been retained in their topic pages. There is no migration guide for this alpha version.

## Stopping point

The batch stops at seven topic pages plus this map. That covers every React conceptual guide without mirroring generated symbols or other framework adapters. Because the package is alpha, future lookups must compare the installed adapter and core versions before reusing these pages.

## Sources

- [Official Hotkeys llms.txt](https://tanstack.com/hotkeys/latest/llms.txt)
- [Immutable documentation tree](https://github.com/TanStack/hotkeys/tree/c73a3a167c979d500e1008341ecad096a6c4e635/docs)
- [Pinned React package manifest](https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/packages/react-hotkeys/package.json)

