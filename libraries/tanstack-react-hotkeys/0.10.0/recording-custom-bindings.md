---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "recording custom bindings"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/hotkey-recording.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Recording custom bindings

`useHotkeyRecorder` supports settings UIs where a user presses a chord to choose a shortcut. The returned recorder object exposes recording state and controls to start, cancel, and clear. Modifier-only presses wait for a non-modifier key rather than committing an incomplete binding. Escape cancels.

Input interception defaults to conservative behavior. With `ignoreInputs: true`, typing in inputs, textareas, selects, and editable content passes through; Escape can still cancel. Set `ignoreInputs: false` only when the recording control intentionally captures keystrokes from within an editable element. Make the active recording state visible and provide a pointer-accessible way to cancel or clear.

Recorded shortcuts are normalized into a portable `Mod` representation when possible. Store that canonical value, not the platform-specific label shown to the current user. Validate and check conflicts before publishing a new command assignment. A recording UI should distinguish an invalid chord, a reserved/browser collision, an application conflict, and a successful binding.

`useHotkeySequenceRecorder` records multiple chords. Enter commits by default, while Escape cancels. Configuration can treat Enter as a normal chord, require manual commit, use alternate commit keys, or finish after idle time. The UI should explain the chosen completion rule; otherwise users cannot tell whether a pause records the sequence or abandons it.

Recording only captures a definition. Register the resulting binding through the normal hotkey or sequence API and keep command metadata with it so menus, help, and conflict checks share one source of truth.

## Sources

- [Hotkey recording guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/hotkey-recording.md)
- [Sequence recording guide](https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/sequence-recording.md)
- [Recorder example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkeyRecorder.md)
- [Sequence-recorder example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkeySequenceRecorder.md)


