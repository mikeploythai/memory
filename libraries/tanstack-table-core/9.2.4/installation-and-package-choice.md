---
library: "@tanstack/table-core"
version: "9.2.4"
topic: "installation and package choice"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/installation.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/table-core@9.2.4 (d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6)"
---

# Installation and package choice

TanStack Table is a headless table engine. Install the adapter for the UI
framework that renders the table. Use `@tanstack/table-core` directly only
when building a framework adapter or a framework-free integration.

## Stable package matrix

The npm `latest` tag was checked independently for each package.

| Runtime | Package | Stable version |
|---|---|---:|
| Framework-free core | `@tanstack/table-core` | `9.2.4` |
| React | `@tanstack/react-table` | `9.2.4` |
| Preact | `@tanstack/preact-table` | `9.2.4` |
| Vue | `@tanstack/vue-table` | `9.2.4` |
| Angular | `@tanstack/angular-table` | `9.2.4` |
| Solid | `@tanstack/solid-table` | `9.2.4` |
| Svelte | `@tanstack/svelte-table` | `9.2.4` |
| Lit | `@tanstack/lit-table` | `9.2.4` |
| Alpine | `@tanstack/alpine-table` | `9.2.4` |
| Ember | `@tanstack/ember-table` | `9.2.4` |
| Octane | `@tanstack/octane-table` | `9.2.4` |

The framework adapters use the core internally. An application normally
installs one adapter, not both the adapter and core explicitly.

## Installation commands

For React:

```sh
npm install @tanstack/react-table@9.2.4
```

For the framework-free package:

```sh
npm install @tanstack/table-core@9.2.4
```

Substitute the matching adapter package from the matrix when using another
framework. Pinning `9.2.4` makes the package agree with this documentation
snapshot; a range may resolve to newer behavior later.

## Optional packages

Table devtools are released separately from the adapters. At retrieval time,
the stable versions were:

| Package group | Stable version |
|---|---:|
| `@tanstack/table-devtools` | `9.2.0` |
| React/Preact/Solid/Vue table devtools | `9.2.0` |
| `@tanstack/match-sorter-utils` | `9.1.2` |

Do not force these packages to `9.2.4`; they do not share the adapter release.
`@tanstack/match-sorter-utils` is useful for fuzzy filtering but is not needed
for a basic table.

## Prerequisites and project creation

The official installation and quick-start pages assume an existing project in
the selected framework. They do not prescribe a project generator, Node.js
range, package-manager version, or universal `dev`/`build` command.

Consequently, package installation is reproducible, but greenfield project
creation remains framework-owned. Preserve the chosen framework's generated
scripts alongside a runnable Table example before calling the bootstrap chain
complete.

## Version-sensitive cautions

- Table v9 is stable. Cached pages that still identify `8.21.3` as npm
  `latest` are stale.
- v8 examples use APIs such as `useReactTable`; v9 documentation centers on
  the v9 feature and state model. Follow the migration guide for upgrades.
- Hosted `/latest` documentation moves. The repository tag in `source_ref` is
  the immutable source for this page.
- Examples in other TanStack repositories may still pin Table v8. Read their
  package manifests before copying code.

## Sources

- https://tanstack.com/table/latest/llms.txt
- https://tanstack.com/table/latest/docs/overview.md
- https://github.com/TanStack/table/tree/%40tanstack%2Ftable-core%409.2.4/docs
- https://github.com/TanStack/table/releases/tag/%40tanstack%2Ftable-core%409.2.4
