---
library: "@tanstack/hotkeys"
version: "0.8.0"
topic: "coverage map"
source: "https://tanstack.com/hotkeys/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# TanStack Hotkeys 0.8.0 coverage map

This bounded set covers the core package and records adapter versions where
their APIs provide the practical application entry points. TanStack labels the
product alpha.

## First-party sources inspected

| Source | Ref or behavior | Result |
|---|---|---|
| [Root TanStack llms index](https://tanstack.com/llms.txt) | moving site index | Identifies product, package, repo, and product index |
| [Hotkeys llms index](https://tanstack.com/hotkeys/latest/llms.txt) | `main` | Complete route inventory used for section mapping |
| [Markdown docs index](https://tanstack.com/hotkeys/latest/docs/index.md) | `main` | Same routing corpus as `llms.txt` |
| `https://tanstack.com/hotkeys/latest/llms-full.txt` | checked 2026-08-31 | Not present; HTTP 404 |
| [Release repository](https://github.com/TanStack/hotkeys/tree/c73a3a167c979d500e1008341ecad096a6c4e635) | immutable commit | Version-sensitive source for core `0.8.0` and adapters |
| [Releases](https://github.com/TanStack/hotkeys/releases) | package tags | Confirms independent package versions |

Hosted `latest` documentation followed repository `main` at
`4f59e1881fc0cc98da7a228160fa90d57bacff60` when checked. It is newer than the
release commit and must not silently override release-pinned signatures.

## Bootstrap chain

| Requirement | Status | Evidence or gap |
|---|---|---|
| Package choice and prerequisites | partial | [Installation](installation-and-first-hotkey.md) maps core and adapters; no runtime/framework/tooling ranges |
| Project creation | not present | No creator or starter command in official Hotkeys docs |
| Installation commands | ready | Core and React npm commands plus complete adapter package map are indexed |
| Getting started / quick start | partial | Five framework quick starts exist; Preact, Solid, and vanilla lack complete quick starts |
| Manual setup | not present | No standalone manual project assembly page |
| Required files and configuration | partial | React hook/provider behavior is indexed under the React adapter, but filenames and application entry wiring are not specified |
| Core mental model | ready | Registration, `Mod`, managers, input defaults, sequences, and scopes are indexed |
| Minimal runnable example | partial | Component snippets are complete locally but depend on an unspecified host app and `saveDocument` implementation |
| Run/build/verification | blocked | No scripts, build command, test command, or automated verification procedure |
| Likely setup mistakes | partial | Adapter/core double-install guidance and target focusability are covered; broader troubleshooting is absent |

## Task readiness

| Task | Status | Indexed evidence |
|---|---|---|
| Greenfield setup | blocked | Missing project creation, prerequisites, filenames, and run/build verification |
| Add common shortcut features | partial | React [registration and sequences](../../tanstack-react-hotkeys/0.10.0/registration-sequences-and-scopes.md) are represented, but exact collection shapes and sequence-recorder commit behavior are deferred; see [recording/state/formatting](../../tanstack-react-hotkeys/0.10.0/recording-key-state-and-formatting.md) |
| Debug registration behavior | partial | Defaults, conflicts, target scope, managers, and devtools are covered; no troubleshooting section |
| Migration | blocked | No official migration guide; package changelogs are not synthesized here |
| Production/build concerns | partial | Devtools production import is documented; no application build or SSR verification |

## Source section mapping

| Substantive source section | Indexed page or status |
|---|---|
| Overview and installation | [installation and package choice](installation-and-first-hotkey.md) |
| Devtools | [core and framework API map](core-and-framework-api-map.md) |
| React, Angular, Vue, Lit, Svelte quick starts | Package and entry-point routing is in [installation and package choice](installation-and-first-hotkey.md); React implementation is indexed under `@tanstack/react-hotkeys@0.10.0`; other adapter implementations are deferred |
| Preact and Solid quick starts | not present upstream |
| Hotkeys guides across seven frameworks | React [registration, sequences, and scopes](../../tanstack-react-hotkeys/0.10.0/registration-sequences-and-scopes.md) is indexed; other framework implementations are deferred |
| Sequence guides across seven frameworks | React sequence registration is indexed in [registration, sequences, and scopes](../../tanstack-react-hotkeys/0.10.0/registration-sequences-and-scopes.md); exact collection signatures and other adapters are deferred |
| Recording and sequence-recording guides | React [recording, key state, and formatting](../../tanstack-react-hotkeys/0.10.0/recording-key-state-and-formatting.md) is partial; exact sequence-recorder commit and timeout contracts are deferred |
| Key-state and formatting guides | React [recording, key state, and formatting](../../tanstack-react-hotkeys/0.10.0/recording-key-state-and-formatting.md) indexes representative hooks and core normalization concepts |
| Core generated API | [core and framework API map](core-and-framework-api-map.md); symbol pages retrieved on demand |
| Seven framework API indexes | [core and framework API map](core-and-framework-api-map.md) |
| Framework examples | representative examples indexed; full gallery deferred |
| Vanilla examples | only display formatting is present upstream; full vanilla workflow not present |

## Recipes, warnings, and operational coverage

| Category | Coverage |
|---|---|
| Common recipes | Multiple shortcuts, conditional bindings, element targets, sequences, held keys, single-hotkey recording, and display labels; sequence-recorder details remain partial |
| Reusable patterns | Provider defaults, portable `Mod`, normalized persisted binding, adapter lifecycle management |
| Warnings / anti-patterns | Avoid assuming package versions match; avoid storing display labels; do not ignore focusability and input defaults |
| Troubleshooting | not present as a dedicated official section; partial diagnostics through devtools and conflict warnings |
| Migrations | not present; breaking-change history remains in per-package changelogs/releases |
| API reference | core and seven framework indexes mapped; generated symbol pages intentionally deferred |
| Production | React production devtools import documented; no complete production build guidance |
| Accessibility | no dedicated guide; focus and recorder cautions are noted without inventing policy |

## Version and package mismatches

| Package | Version |
|---|---:|
| `@tanstack/hotkeys` | `0.8.0` |
| React, Preact, Solid, Svelte, Vue, Angular adapters | `0.10.0` |
| Lit adapter | `0.11.0` |
| `@tanstack/hotkeys-devtools` | `0.9.0` |
| React, Preact, Solid, Vue devtools adapters | `0.7.0` |

Core pages remain under `tanstack-hotkeys/0.8.0`. React implementation pages
use `tanstack-react-hotkeys/0.10.0`; other adapter versions are recorded in the
package map but do not inherit the core identity. Hosted docs are unversioned
`v0/main`, so release source must win for exact signatures.

## Meaningful gaps

- No complete greenfield bootstrap or verification command.
- No Preact, Solid, or vanilla quick start.
- No migration, troubleshooting, compatibility matrix, or dedicated
  accessibility section.
- No product-level `llms-full.txt`.
- Current hosted prose may contain changes after the release commit.

## Bounded stopping point

This batch covers core package choice and API routing plus React registration,
sequences, recording, key state, and display normalization. It defers exact
sequence-recorder commit behavior, collection signatures, the example gallery,
other framework implementations, generated symbol pages, and changelog
synthesis. Task readiness remains partial wherever those details are required.
