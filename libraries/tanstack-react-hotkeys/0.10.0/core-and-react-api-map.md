---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "core and React API map"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/reference/index.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Core and React API map

`@tanstack/react-hotkeys` 0.10.0 wraps the separately versioned `@tanstack/hotkeys` core package, which is 0.8.0 at this release boundary. Record both versions when a task depends on a core class or utility rather than a React hook.

The core reference groups APIs by responsibility. Registration uses `HotkeyManager`, `getHotkeyManager`, options, callbacks, metadata, registration handles, conflict behavior, parsing, matching, and handler factories. Sequences use `SequenceManager`, sequence options and handles, and `createSequenceMatcher`. Held-key behavior uses `KeyStateTracker` and its state types. Recorder classes cover chords and sequences. Normalization, parsing, validation, platform detection, key constants, and formatting utilities form the portable-data layer.

The React reference adds `useHotkey`, `useHotkeys`, provider/default hooks, registration introspection, sequence hooks, held-key hooks, `useKeyHold`, and both recorder hooks. Use plural hooks for data-driven lists so hook order remains stable. The provider sets shared defaults; individual hooks own registration cleanup.

Generated symbol pages are the authority for exact parameter and return types. The guides explain defaults and interaction behavior that signatures cannot express, including input filtering, propagation, conflict warnings, timeout rules, recorder completion, blur cleanup, and canonical `Mod` storage.

This package is alpha. Do not infer compatibility across minor versions. When upgrading, compare both adapter and core package versions and reread the generated reference for renamed hooks, option defaults, and changed recorder/manager types.

## Sources

- [React hooks reference](https://tanstack.com/hotkeys/latest/docs/framework/react/reference/index.md)
- [Core reference](https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/reference/index.md)
- [Pinned React package manifest](https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/packages/react-hotkeys/package.json)


