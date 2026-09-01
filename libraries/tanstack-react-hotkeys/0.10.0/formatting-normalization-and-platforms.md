---
library: "@tanstack/react-hotkeys"
version: "0.10.0"
topic: "formatting normalization and platforms"
source: "https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/framework/react/guides/formatting-display.md"
retrieved_at: "2026-08-31"
source_ref: "c73a3a167c979d500e1008341ecad096a6c4e635"
---

# Formatting, normalization, and platforms

Store canonical shortcut definitions and format them only for display. `normalizeHotkey` and `normalizeRegisterableHotkey` produce ordered definitions and preserve portable `Mod` when the platform mapping permits it. Expanding `Mod` to `Meta` before persistence makes the saved binding macOS-specific; expanding it to `Control` makes it Windows/Linux-specific.

`formatForDisplay` is the primary platform-aware formatter. It uses familiar macOS symbols and text labels on Windows/Linux. The platform option affects normalization as well as display. If one parsed shortcut must be shown for several platforms, first serialize it using the platform under which it was parsed, then format that canonical string for each target platform.

Parsing converts a string into modifier flags and a key. Normalization turns parsed or event-derived input back into canonical order. Validation reports invalid syntax and potential platform issues. Validate user-provided or migrated strings before registering them; TypeScript autocomplete protects literals in source code but cannot validate stored runtime data.

Prefer `Mod` in documentation, command metadata, persistence, and registration. Use formatted output in menus, command palettes, help screens, and recorder UI. Do not store glyph strings such as a macOS Command symbol as the command definition.

Keyboard layouts and locales can produce different `event.key` values. The library primarily uses `event.key` and falls back to `event.code` for documented letter/digit cases. Test punctuation-heavy shortcuts and Alt/Option combinations on the layouts the product supports.

## Sources

- [Formatting and display guide](https://tanstack.com/hotkeys/latest/docs/framework/react/guides/formatting-display.md)
- [Core normalization and formatting API](https://github.com/TanStack/hotkeys/blob/c73a3a167c979d500e1008341ecad096a6c4e635/docs/reference/index.md)


