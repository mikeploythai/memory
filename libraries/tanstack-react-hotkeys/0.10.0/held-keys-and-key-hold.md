---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "held keys and key hold"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/key-state-tracking.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Held keys and key-hold interactions

`useHeldKeys` returns the logical keys currently held, while `useHeldKeyCodes` exposes physical keyboard codes. Choose logical keys for command semantics and codes when physical position matters. `useKeyHold` adds duration-aware behavior for press-and-hold interactions.

Common patterns include hold-to-reveal controls, momentary modes, keyboard hints, and diagnostic displays. A hold interaction should also have a pointer or touch equivalent when it controls essential behavior. Avoid using held state as a hidden prerequisite that keyboard users cannot discover.

The shared `KeyStateTracker` handles browser and platform cleanup. When the window loses focus, it clears held keys so keys released in another application do not remain “stuck” in local state. macOS modifier behavior has additional edge cases handled by the tracker. Do not rebuild this state with independent component-level `keydown` and `keyup` sets unless the library cannot represent the needed interaction.

Key-repeat events are different from hold duration. A repeated `keydown` can fire many callbacks, while `useKeyHold` models how long a key remains pressed. Use `requireReset` for one-shot shortcuts and the hold API for duration-based actions.

Keep the tracker lifecycle application-wide when many components consume held state. Multiple ad hoc listeners make blur cleanup and event ordering harder to reason about. For debugging, format logical keys and codes separately so keyboard-layout behavior is visible.

## Sources

- [Key-state tracking guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/key-state-tracking.md)
- [useHeldKeys example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useHeldKeys.md)
- [useKeyHold example](https://tanstack.com/hotkeys/latest/docs/framework/react/examples/useKeyhold.md)


