---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "registration options and conflicts"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/hotkeys.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Registration options and conflicts

`useHotkey` registers one shortcut with automatic React lifecycle cleanup and stale-closure protection. `useHotkeys` registers a data-driven list without calling hooks in a loop. Bindings may be typed strings or raw objects. Use `Mod` for a portable Command-on-macOS and Control-on-Windows/Linux shortcut.

The defaults are intentionally active: registrations are enabled, listen on `keydown`, call both `preventDefault()` and `stopPropagation()`, and warn on conflicts. Do not assume the browser's native action or ancestor keyboard handler will still run. Opt out explicitly when a shortcut should coexist with them. Set `requireReset` when key repeat should not retrigger the callback until release.

Input filtering uses a smart default. Single keys and Shift/Alt-only combinations are normally ignored in text inputs, textareas, selects, and editable content, while Control/Meta shortcuts and Escape may still fire. Button-like inputs are treated differently from text-entry controls. Set `ignoreInputs` explicitly when the product requires a stricter policy.

Duplicate bindings warn but remain registered under the default conflict behavior. Treat the warning as a design problem: define which scope or component owns the command, disable inactive bindings, or select a different conflict policy. Metadata can label registrations for a shortcut palette or devtools without changing execution.

Dynamic `useHotkeys` arrays are diffed using array position plus normalized binding. Reordering can unregister and register entries even when callbacks are otherwise stable. Keep list order stable and use one data source for command definitions.

## Sources

- [React hotkeys guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/hotkeys.md)
- [React useHotkey example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkey.md)
- [React useHotkeys example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHotkeys.md)


