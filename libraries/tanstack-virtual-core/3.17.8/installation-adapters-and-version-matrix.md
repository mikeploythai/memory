---
library: "@tanstack/virtual-core"
version: "3.17.8"
topic: "installation adapters and version matrix"
source: "https://github.com/TanStack/virtual/blob/e9874f033c74afd3251eeb9f3e60b2530cc7ae88/docs/installation.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/virtual-core@3.17.8 (e9874f033c74afd3251eeb9f3e60b2530cc7ae88)"
---

# Installation, adapters, and version matrix

TanStack Virtual calculates which items should be rendered in a scrollable
area. Install the framework adapter used by the view. Use the core directly for
framework-free rendering or adapter development.

## Stable package versions

Virtual packages do not share one release number. Each npm `latest` tag was
checked independently.

| Runtime | Package | Stable version |
|---|---|---:|
| Core | `@tanstack/virtual-core` | `3.17.8` |
| React | `@tanstack/react-virtual` | `3.14.10` |
| Solid | `@tanstack/solid-virtual` | `3.13.37` |
| Lit | `@tanstack/lit-virtual` | `3.13.37` |
| Vue | `@tanstack/vue-virtual` | `3.13.36` |
| Svelte | `@tanstack/svelte-virtual` | `3.13.36` |
| Marko | `@tanstack/marko-virtual` | `3.15.1` |
| Angular | `@tanstack/angular-virtual` | `6.0.3` |

The adapter's version is not evidence for the bundled core version. Read its
published manifest or lockfile when dependency resolution matters.

## Installation commands

React:

```sh
npm install @tanstack/react-virtual@3.14.10
```

Framework-free core:

```sh
npm install @tanstack/virtual-core@3.17.8
```

Other adapters use the package and stable version shown above. Avoid a blanket
workspace override that forces all Virtual packages to `3.17.8`.

## Adapter entry points

- React exposes element and window virtualizer hooks.
- Solid, Vue, Svelte, Lit, Angular, and Marko expose bindings suitable for
  their reactive and rendering models.
- The core exposes `Virtualizer`, observers, scroll helpers, and measurement
  utilities without rendering components.

Use the framework page as the API authority for adapter names:

- https://tanstack.com/virtual/latest/docs/framework/react/react-virtual.md
- https://tanstack.com/virtual/latest/docs/framework/angular/angular-virtual.md
- https://tanstack.com/virtual/latest/docs/framework/solid/solid-virtual.md
- https://tanstack.com/virtual/latest/docs/framework/svelte/svelte-virtual.md
- https://tanstack.com/virtual/latest/docs/framework/vue/vue-virtual.md
- https://tanstack.com/virtual/latest/docs/framework/marko/marko-virtual.md
- https://tanstack.com/virtual/latest/docs/framework/lit/lit-virtual.md

## Prerequisites and setup boundary

The official docs assume an existing framework application with a scrollable
element. They do not supply a universal project generator, runtime range,
entry-file layout, styling system, or build command.

Virtualization also depends on layout. The scrolling element needs a bounded
size and overflow behavior, while a child size container represents the total
virtual size. These are application CSS decisions, not installed defaults.

## Example version caution

Every retained example should include its `package.json`. For example, the
official Svelte table example currently pins `@tanstack/svelte-table` on a v8
line and `@tanstack/svelte-virtual` on `3.13.36`. Copying source without that
manifest can silently combine incompatible generations.

## Sources

- https://tanstack.com/virtual/latest/llms.txt
- https://github.com/TanStack/virtual/tree/%40tanstack%2Fvirtual-core%403.17.8/docs
- https://github.com/TanStack/virtual/releases/tag/%40tanstack%2Fvirtual-core%403.17.8
- https://github.com/TanStack/virtual/blob/main/examples/svelte/table/package.json

## Gaps

There is no dedicated quick-start page or common verification command. The Lit
adapter page exists in the release tree but is omitted from the llms index's
Get Started list.
