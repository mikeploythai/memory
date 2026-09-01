---
library: "@tanstack/hotkeys"
version: "0.8.0"
topic: "core and framework API map"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/reference/index.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Core and framework API map

Use this page to choose the correct reference area. It is not a substitute for
the symbol-level generated API pages when an exact signature matters.

## Package versions

| Package family | Version |
|---|---:|
| `@tanstack/hotkeys` | `0.8.0` |
| React, Preact, Solid, Svelte, Vue, Angular adapters | `0.10.0` |
| Lit adapter | `0.11.0` |
| `@tanstack/hotkeys-devtools` | `0.9.0` |
| React, Preact, Solid, Vue devtools adapters | `0.7.0` |

All listed releases resolve to repository commit `c73a3a1`, but package
versions are independent and must remain explicit.

## Core API areas

| Area | Principal symbols |
|---|---|
| Registration | `HotkeyManager`, `getHotkeyManager`, `HotkeyOptions`, registration handles/views |
| Sequences | `SequenceManager`, `getSequenceManager`, `SequenceOptions`, `createSequenceMatcher` |
| Key state | `KeyStateTracker`, `getKeyStateTracker`, `KeyStateTrackerState` |
| Recording | `HotkeyRecorder`, `HotkeySequenceRecorder`, option and state interfaces |
| Parsing and matching | `parseHotkey`, `parseKeyboardEvent`, `matchesKeyboardEvent`, `checkHotkey` |
| Normalization | `normalizeHotkey`, event/parsed/registerable variants, `resolveModifier` |
| Validation | `validateHotkey`, `assertValidHotkey`, key predicates |
| Display | `formatForDisplay`, `formatHotkey`, `formatHotkeySequence`, label constants |
| Types and constants | hotkey strings, raw/parsed types, key sets, modifier aliases/order |

Generated core index:
[Core API](https://tanstack.com/hotkeys/latest/docs/reference/index.md).

## Framework entry points

| Framework | Registration style | Reference |
|---|---|---|
| React | hooks and `HotkeysProvider` | [React API](https://tanstack.com/hotkeys/latest/docs/framework/react/reference/index.md) |
| Preact | hooks and `HotkeysProvider` | [Preact API](https://tanstack.com/hotkeys/latest/docs/framework/preact/reference/index.md) |
| Solid | `create*` primitives | [Solid API](https://tanstack.com/hotkeys/latest/docs/framework/solid/reference/index.md) |
| Angular | `inject*` APIs and `provideHotkeys` | [Angular API](https://tanstack.com/hotkeys/latest/docs/framework/angular/reference/index.md) |
| Vue | composables and context provider | [Vue API](https://tanstack.com/hotkeys/latest/docs/framework/vue/reference/index.md) |
| Lit | decorators and reactive controllers | [Lit API](https://tanstack.com/hotkeys/latest/docs/framework/lit/reference/index.md) |
| Svelte | creators, attachments, context, state wrappers | [Svelte API](https://tanstack.com/hotkeys/latest/docs/framework/svelte/reference/index.md) |

## React mapping

| Concern | React API |
|---|---|
| One or many hotkeys | `useHotkey`, `useHotkeys` |
| One or many sequences | `useHotkeySequence`, `useHotkeySequences` |
| Record a hotkey | `useHotkeyRecorder` |
| Record a sequence | `useHotkeySequenceRecorder` |
| Held keys | `useHeldKeys`, `useHeldKeyCodes`, `useKeyHold` |
| Defaults | `HotkeysProvider`, `useDefaultHotkeysOptions` |
| Inspection | `useHotkeyRegistrations` |

React symbol index:
[React hooks](https://tanstack.com/hotkeys/latest/docs/framework/react/reference/index.md).

## Core versus adapter

Use core directly for vanilla JavaScript or when manually managing manager
lifecycles. Use an adapter in a component application for registration cleanup,
reactive state, current callback handling, and framework-native refs or targets.
Each adapter re-exports core, so separate core installation is normally
unnecessary.

## Devtools API

The documented integrations are:

- React: `@tanstack/react-devtools` plus `@tanstack/react-hotkeys-devtools`;
- Preact: `@tanstack/preact-devtools` plus `@tanstack/preact-hotkeys-devtools`;
- Solid: `@tanstack/solid-devtools` plus `@tanstack/solid-hotkeys-devtools`;
- Vue: `@tanstack/vue-hotkeys-devtools` panel component.

Angular and Lit have no dedicated Hotkeys devtools adapter in the documented
package map. The React plugin exposes a `/production` import when devtools must
be deliberately included in production.

## Reference cautions

- Hosted `latest` API pages follow repository `main`, not an immutable package
  version.
- The release-pinned commit is the authority for `0.8.0` signatures.
- Generated symbol pages are numerous and should be retrieved only for the
  symbol being implemented or debugged.
- No official migration reference maps breaking changes between releases.

## Sources

- [Official docs index](https://tanstack.com/hotkeys/latest/llms.txt)
- [Core API index](https://tanstack.com/hotkeys/latest/docs/reference/index.md)
- [Devtools](https://tanstack.com/hotkeys/latest/docs/devtools.md)
- [Release-pinned packages](https://github.com/TanStack/hotkeys/tree/c73a3a167c979d500e1008341ecad096a6c4e635/packages)
- [Release tag](https://github.com/TanStack/hotkeys/releases/tag/%40tanstack%2Fhotkeys%400.8.0)
