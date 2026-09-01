---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "recording key state and formatting"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/hotkey-recording.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Recording, key state, and formatting

The React adapter provides separate APIs for recording user-configurable
bindings, observing held keys, and formatting portable bindings for display.
These examples target `@tanstack/react-hotkeys@0.10.0`. Do not treat recorder
APIs as normal shortcut registrations.

## Record a shortcut

In React, `useHotkeyRecorder` creates a recorder whose lifecycle follows the
component:

```tsx
import { useHotkeyRecorder } from '@tanstack/react-hotkeys'

function ShortcutEditor() {
  const recorder = useHotkeyRecorder({
    onRecord: (hotkey) => {
      console.log('Recorded:', hotkey)
    },
    onCancel: () => {
      console.log('Recording cancelled')
    },
  })

  return (
    <button onClick={() => recorder.startRecording()}>
      {recorder.isRecording ? 'Recording…' : 'Record shortcut'}
    </button>
  )
}
```

Use the recorder state and callbacks to build a settings UI. Persist the
normalized result as application data; the documentation does not prescribe a
storage format or migration strategy for saved user bindings.

## Record a sequence

`useHotkeySequenceRecorder` captures ordered multi-key bindings separately
from single hotkeys. Its options include commit behavior and timeout-related
state. Consult the exact API reference before choosing commit keys because the
library is alpha.

```tsx
import { useHotkeySequenceRecorder } from '@tanstack/react-hotkeys'

const recorder = useHotkeySequenceRecorder({
  onRecord: (sequence) => console.log(sequence),
})
```

## Observe held keys

`useHeldKeys` returns currently held key values. `useHeldKeyCodes` exposes
physical code-oriented state, and `useKeyHold` answers whether one key is held.

```tsx
import { useHeldKeys, useKeyHold } from '@tanstack/react-hotkeys'

function StatusBar() {
  const heldKeys = useHeldKeys()
  const isShiftHeld = useKeyHold('Shift')

  return (
    <div>
      {isShiftHeld && <span>Shift mode active</span>}
      {heldKeys.length > 0 && <span>{heldKeys.join('+')}</span>}
    </div>
  )
}
```

At core level, `KeyStateTracker` and `getKeyStateTracker()` provide the shared
tracking mechanism. Use framework APIs when lifecycle and reactive rendering
matter.

## Format a portable binding

`formatForDisplay` converts a portable binding into a platform-oriented label:

```tsx
import { formatForDisplay, useHotkey } from '@tanstack/react-hotkeys'

function SaveButton() {
  useHotkey('Mod+S', () => save())

  return (
    <button>
      Save <kbd>{formatForDisplay('Mod+S')}</kbd>
    </button>
  )
}
```

The React quick start documents `⌘S` on macOS and `Ctrl+S` on Windows for this
example. Core formatting APIs also cover sequences, normalization, modifier
labels, and punctuation labels.

## Normalize before persistence or comparison

The core API separates several operations:

- `parseHotkey` parses string syntax;
- `normalizeHotkey` produces a canonical string;
- `normalizeHotkeyFromEvent` derives a binding from an event;
- `normalizeRegisterableHotkey` prepares a string or raw object for use;
- `formatForDisplay` creates a user-facing platform label;
- `validateHotkey` and `assertValidHotkey` check validity.

Store a portable normalized binding, not the platform-specific display label.
Display formatting can then adapt `Mod` for the current platform.

## Input and capture cautions

Recording is an interactive mode. The application remains responsible for:

- giving the recording control a visible state and accessible name;
- offering a clear cancel path;
- detecting application-level conflicts before saving;
- deciding how reserved browser or operating-system shortcuts are handled;
- testing non-US layouts and assistive technology interactions.

The official docs describe recorder callbacks and state but do not supply a
complete accessible settings form, persistence schema, conflict-resolution
workflow, or cross-version migration format.

## Sources

- [Hotkey recording guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/hotkey-recording.md)
- [Sequence recording guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/sequence-recording.md)
- [Key-state tracking guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/key-state-tracking.md)
- [Formatting and display guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/formatting-display.md)
- [Core HotkeyRecorder API](https://tanstack.com/hotkeys/latest/docs/reference/classes/HotkeyRecorder.md)
- [Core KeyStateTracker API](https://tanstack.com/hotkeys/latest/docs/reference/classes/KeyStateTracker.md)
- [Release repository](https://github.com/TanStack/hotkeys/tree/c73a3a167c979d500e1008341ecad096a6c4e635)
