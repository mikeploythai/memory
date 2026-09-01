---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "registration sequences and scopes"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/hotkeys.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Registration, sequences, and scopes

This page covers the React adapter's lifecycle-aware registration APIs at
`0.10.0`. Other adapters expose the same core concepts through independently
versioned framework APIs.

## Register one shortcut

```tsx
import { useHotkey } from '@tanstack/react-hotkeys'

function Editor() {
  useHotkey('Mod+S', () => saveDocument())
  return <div>Editor</div>
}
```

The callback receives the original `KeyboardEvent` and a context containing
the normalized hotkey and parsed representation:

```tsx
useHotkey('Mod+S', (event, context) => {
  console.log(context.hotkey)
  console.log(context.parsedHotkey)
})
```

A registration may use a string or a `RawHotkey` object. Prefer `Mod` for a
portable Command/Control binding.

## Default event behavior

The documented defaults are opinionated:

- `enabled` defaults to `true`;
- `preventDefault` defaults to `true`;
- `stopPropagation` defaults to `true`;
- input filtering allows Control/Meta shortcuts and Escape in inputs while
  suppressing ordinary typing-oriented shortcuts;
- duplicate registrations use `conflictBehavior: 'warn'` by default.

Override browser behavior deliberately:

```tsx
useHotkey('Mod+S', () => saveDocument(), {
  preventDefault: false,
  stopPropagation: false,
})
```

Disabled shortcuts remain registered and visible to devtools; execution is
suppressed without unregistering and re-registering the binding.

## Conditional registration

```tsx
function Modal(props: { isOpen: boolean; onClose: () => void }) {
  useHotkey('Escape', props.onClose, { enabled: props.isOpen })
  if (!props.isOpen) return null
  return <div role="dialog">Dialog</div>
}
```

## Scope a shortcut to an element

Pass a target ref when the binding should only run while a particular subtree
has focus:

```tsx
import { useRef } from 'react'
import { useHotkey } from '@tanstack/react-hotkeys'

function Panel() {
  const panelRef = useRef<HTMLDivElement>(null)
  useHotkey('Escape', () => closePanel(), { target: panelRef })

  return (
    <div ref={panelRef} tabIndex={0}>
      Press Escape while this panel has focus
    </div>
  )
}
```

The target must be focusable when users need to move focus to it. Scope does
not replace appropriate focus management or accessible keyboard design.

## Register multiple shortcuts

Separate `useHotkey` calls are independent:

```tsx
useHotkey('Mod+S', () => save())
useHotkey('Mod+Z', () => undo())
useHotkey('Mod+Shift+Z', () => redo())
useHotkey('Escape', () => closeDialog())
```

The adapter also exposes `useHotkeys` for definition collections. Consult its
version-pinned API reference before depending on its exact definition shape.

## Multi-key sequences

`useHotkeySequence` registers ordered shortcuts such as Vim-style commands:

```tsx
import { useHotkeySequence } from '@tanstack/react-hotkeys'

function Navigation() {
  useHotkeySequence(['G', 'G'], () => scrollToTop())
  useHotkeySequence(['G', 'Shift+G'], () => scrollToBottom())
  return null
}
```

Sequence matching has a configurable timeout. Provider defaults can set
`hotkeySequence: { timeout: 1500 }`; per-registration options override it.

## Core APIs behind adapters

The framework hooks wrap singleton managers with lifecycle cleanup:

- `HotkeyManager` / `getHotkeyManager()` manage normal registrations;
- `SequenceManager` / `getSequenceManager()` manage ordered sequences;
- registration handles support controlled teardown and inspection;
- registration views expose safe data for devtools and UI inspection.

## Known limits

The official guides do not provide a browser-reserved shortcut matrix,
complete locale/keyboard-layout compatibility table, or accessibility recipe
for every shortcut pattern. The overview explicitly says edge cases vary by
layout, locale, and operating system. Test the target environments.

## Sources

- [React hotkeys guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/hotkeys.md)
- [React sequences guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/sequences.md)
- [Core HotkeyManager API](https://tanstack.com/hotkeys/latest/docs/reference/classes/HotkeyManager.md)
- [Core SequenceManager API](https://tanstack.com/hotkeys/latest/docs/reference/classes/SequenceManager.md)
- [Release repository](https://github.com/TanStack/hotkeys/tree/c73a3a167c979d500e1008341ecad096a6c4e635)
