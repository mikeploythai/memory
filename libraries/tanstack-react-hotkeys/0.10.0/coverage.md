---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "coverage map"
source: "https://tanstack.com/hotkeys/latest/llms.txt"
retrieved_at: "2026-09-07"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# TanStack React Hotkeys 0.10.0 coverage map

This map covers the independently versioned React adapter. Core package
selection and installation evidence remains in the `@tanstack/hotkeys` map.

## First-party indices and refs inspected

| Source | Result |
|---|---|
| https://tanstack.com/hotkeys/latest/llms.txt | Moving index used to inventory React quick starts, guides, and references |
| https://github.com/TanStack/hotkeys/tree/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react | Immutable React documentation tree |

## Bootstrap chain

| Requirement | Status | Evidence or gap |
|---|---|---|
| Package choice and prerequisites | partial | The [core installation page](../../tanstack-hotkeys/0.8.0/installation-and-first-hotkey.md) pairs React adapter `0.10.0` with core `0.8.0`; React and tooling ranges are not prescribed |
| Project creation | not applicable | Hotkeys assumes an existing React application |
| Installation | partial | The React package choice and npm command are indexed in the core installation page, but the command is unpinned |
| Required files and configuration | partial | `useHotkey` works without a provider for the retained cases; entry wiring and host scripts are external |
| Getting started and mental model | ready | [Registration, sequences, and scopes](registration-sequences-and-scopes.md) covers lifecycle registration, defaults, conflicts, and `Mod` |
| Minimal runnable application | partial | Complete component snippets exist but call application-owned actions and assume a host app |
| Run/build verification | blocked | No project scripts or automated browser verification procedure are indexed |
| Setup mistakes and version caveats | partial | Input filtering, browser behavior, focus scope, layout variability, and alpha stability are covered |

Greenfield setup is blocked by the missing host application and run/build
verification. Common shortcut work in an existing React application is partial.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Greenfield React application | blocked | No project creation, entry files, or build verification |
| Add common shortcuts and sequences | partial | [Registration and sequences](registration-sequences-and-scopes.md); host integration and browser verification remain external |
| Record and display user-defined shortcuts | partial | [Recording, state, and formatting](recording-key-state-and-formatting.md); persistence and conflict resolution remain application-owned |
| Debug registration behavior | partial | Defaults and conflict behavior are indexed; no dedicated troubleshooting workflow |
| Migration | blocked | No first-party migration guide; changelogs are not synthesized here |
| Production/build concerns | partial | Browser and input caveats are retained; host build and SSR behavior are unverified |

## Source coverage

| Source area | Status | Memory page or gap |
|---|---|---|
| Installation and package/version choice | indexed | Core [installation and first hotkey](../../tanstack-hotkeys/0.8.0/installation-and-first-hotkey.md) |
| React hotkey registration, options, conflicts, targets, and sequences | indexed | [Registration, sequences, and scopes](registration-sequences-and-scopes.md) |
| Recording, held keys, key state, normalization, and display formatting | indexed | [Recording, key state, and formatting](recording-key-state-and-formatting.md) |
| Provider configuration and devtools | deferred | Concepts are referenced by the core map; exact adapter setup is not retained here |
| Complete `useHotkeys` collection shape and generated API signatures | deferred | Retrieve the pinned generated reference before implementation |
| Accessibility recipes and cross-layout compatibility matrix | not present | The official docs leave these to application testing |
| Migration guide | not present | No dedicated first-party section found |

## Patterns, warnings, and stopping point

The retained pages cover portable `Mod` bindings, scoped focus targets,
conditional registration, sequence timeouts, recorder separation, and storage
of normalized rather than display-formatted bindings. This audit adds the
missing adapter coverage map only.

## Sources

- https://github.com/TanStack/hotkeys/tree/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react

