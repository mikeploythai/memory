---
library: "@tanstack/react-pacer"
version: "0.23.0"
topic: "react hooks and provider patterns"
source: "https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/framework/react/adapter.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-pacer@0.23.0"
---

# React hooks and provider patterns

The React adapter offers callback hooks, value/state helpers, and instance hooks for each timing policy. Callback hooks are concise event wrappers; value/state helpers delay or pace derived values; instance hooks expose the full utility and store. `PacerProvider` supplies shared defaults without replacing per-instance policy.

## Version boundary

These pages target `@tanstack/react-pacer` 0.23.0. The exact release pairs it with core `@tanstack/pacer` 0.22.0. Core classes, options, state, and timing semantics therefore use 0.22.0 behavior.

## Implementation guidance

- Select the lowest abstraction that exposes the state and controls the component needs.
- Keep callbacks and option objects stable or use the adapter patterns documented for updates.
- Use provider defaults for cross-cutting settings, then override locally where product policy differs.
- Clean up pending work on unmount or use the documented unmount callback.

## Constraints and failure modes

- Creating a new pacer instance on every render resets timing and state.
- A delayed state update can target an unmounted or semantically changed component.
- Global defaults can silently alter unrelated interactions if their scope is too broad.
- A value helper is not a substitute for queueing when every intermediate value must be processed.

## Retrieval cues

Use this page when work mentions react hooks and provider patterns, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/framework/react/adapter.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/framework/react/reference/index.md
- https://github.com/TanStack/pacer/blob/%40tanstack%2Freact-pacer%400.23.0/docs/framework/react/reference/functions/PacerProvider.md

