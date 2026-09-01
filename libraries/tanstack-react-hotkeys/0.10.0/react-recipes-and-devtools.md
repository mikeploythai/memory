---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "React recipes and devtools"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/devtools.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# React recipes and devtools

The official examples cover one shortcut, a dynamic shortcut list, one sequence, multiple sequences, chord recording, sequence recording, held-key display, and press-and-hold behavior. Use them as executable wiring references and keep command definitions separate from presentation so the same metadata can drive registration, menus, help, and settings.

A command palette or shortcut help screen can read live registrations through the registration hook. Attach names and descriptions as metadata rather than maintaining a second lookup table. Disabled registrations remain visible, which helps explain context-dependent commands.

Use the provider for application-wide defaults such as input filtering, conflict behavior, and sequence timeout. Per-hook options should express real exceptions, not repeat the global policy. Target-specific registrations can attach to an element or document scope; ensure the target exists for the registration lifecycle.

Devtools expose registered hotkeys, sequences, and held-key state. They are useful for finding duplicate registrations, unexpected disabled state, conflicting targets, and bindings that remain active in inputs. Keep devtools development-only unless the product intentionally offers a diagnostics panel.

For customizable shortcuts, use one command registry containing a stable command ID, callback, metadata, default binding, and user override. Normalize and validate the override, check conflicts, then derive both registration and display from it. Avoid conditionally calling a hook for each command; pass a stable array to the plural hook and control activation through `enabled`.

## Sources

- [Devtools guide](https://tanstack.com/hotkeys/latest/docs/devtools.md)
- [useHotkey example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkey.md)
- [useHotkeys example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkeys.md)
- [Recorder example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkeyRecorder.md)
- [Held-keys example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHeldKeys.md)


