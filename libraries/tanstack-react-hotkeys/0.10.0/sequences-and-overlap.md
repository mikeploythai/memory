---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "sequences and overlap"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/sequences.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Sequences and overlap

`useHotkeySequence` registers an ordered list of chords, such as a Vim-style command. Every step must arrive in order within the configured timeout. `useHotkeySequences` handles a data-driven list without conditional or looped hook calls. Provider defaults can establish a shared timeout, while an individual sequence can override it.

Choose the timeout for the interaction rather than using one value blindly. Short repeated-key commands may need a tight window; longer mnemonic sequences need more time. When the timeout expires, progress resets. A wrong non-modifier step also resets matching. Modifier-only keydown events between steps are ignored, allowing a user to press or hold Shift, Control, Alt, or Meta before the next chord without breaking progress.

Sequences may contain modifier chords and can overlap. An initial prefix can therefore match more than one registration. Document which command wins or waits, test the ambiguous prefix, and avoid a dense command grammar whose only distinction is timing. Metadata should identify each sequence in help and diagnostic views.

The singleton sequence manager stores registrations and progress. React hooks manage registration cleanup, so do not also register the same sequence imperatively unless two callbacks are intentional. Disabled sequences remain available for introspection while execution is suppressed.

Test sequences with real keyboard events on target operating systems. Locale and layout differences affect the keys users can produce, while the core matching model is based primarily on `event.key` with documented fallbacks.

## Sources

- [Sequences guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/sequences.md)
- [Single-sequence example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkeySequence.md)
- [Multiple-sequences example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkeySequences.md)


