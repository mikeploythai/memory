---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "cross-platform React hotkeys"
source: "https://tanstack.com/hotkeys/latest/docs/framework/react/quick-start"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-hotkeys@0.10.0; release commit c73a3a1; alpha"
---

# Cross-platform hotkeys in React

TanStack Hotkeys supplies a framework-independent core and a React adapter. Version 0.10.0 is alpha software, so pin the package and recheck the moving documentation before upgrades.

## Installation

```sh
npm install @tanstack/react-hotkeys
```

The React package re-exports the core APIs. It supports React and ReactDOM 16.8 or newer and declares Node 18 or newer.

## Register a shortcut

```tsx
import { useHotkey } from '@tanstack/react-hotkeys'

export function SaveShortcut({
  enabled,
  onSave,
}: {
  enabled: boolean
  onSave: () => void
}) {
  useHotkey('Mod+S', onSave, { enabled })
  return <p>Use Command+S on macOS or Control+S elsewhere.</p>
}
```

`Mod` maps to Meta/Command on macOS and Control on Windows and Linux. Options can conditionally enable a shortcut or scope it to a DOM element or React ref.

## Notes

- The default behavior prevents the browser default action and stops propagation.
- Register familiar browser shortcuts deliberately because they can replace browser behavior.
- Single-key shortcuts are normally ignored in text-entry controls; modifier shortcuts and Escape follow context-sensitive defaults.
- Add the separate devtools packages only when diagnostic UI is needed.

## Sources

- https://tanstack.com/hotkeys/latest/docs/overview
- https://tanstack.com/hotkeys/latest/docs/installation
- https://tanstack.com/hotkeys/latest/docs/framework/react/guides/hotkeys
- https://github.com/TanStack/hotkeys/releases
