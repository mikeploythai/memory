---
library: "@tanstack/form-core"
version: "1.33.5"
topic: "installation adapters and version matrix"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/installation.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/form-core@1.33.5 (b865ef335a69aa08a2f160895258f13e03773467)"
---

# Installation, adapters, and version matrix

TanStack Form is headless form state and validation. Applications should
install the adapter for their rendering framework. Use `@tanstack/form-core`
directly for framework-free integrations or adapter development.

## Stable package versions

The packages in this repository are independently published. Their npm
`latest` tags were checked separately.

| Purpose | Package | Stable version |
|---|---|---:|
| Core | `@tanstack/form-core` | `1.33.5` |
| React | `@tanstack/react-form` | `1.33.5` |
| Angular | `@tanstack/angular-form` | `1.33.5` |
| Solid | `@tanstack/solid-form` | `1.33.5` |
| Svelte | `@tanstack/svelte-form` | `1.33.5` |
| Vue | `@tanstack/vue-form` | `1.33.5` |
| Preact | `@tanstack/preact-form` | `1.30.5` |
| Lit | `@tanstack/lit-form` | `1.25.5` |
| React Start | `@tanstack/react-form-start` | `1.33.5` |
| Next.js | `@tanstack/react-form-nextjs` | `1.33.5` |
| Remix | `@tanstack/react-form-remix` | `1.33.5` |
| Core/React/Solid devtools | corresponding devtools package | `0.2.34` |

Do not align Preact, Lit, or devtools to `1.33.5` without checking their own
registries. Their stable release lines differ from the core.

## Installation commands

React:

```sh
npm install @tanstack/react-form@1.33.5
```

Framework-free core:

```sh
npm install @tanstack/form-core@1.33.5
```

The official installation page also documents meta-framework adapters:

```sh
npm install @tanstack/react-form-start@1.33.5
npm install @tanstack/react-form-nextjs@1.33.5
npm install @tanstack/react-form-remix@1.33.5
```

Install only the integration used by the application.

## React devtools

The documented React devtools setup uses the shared TanStack Devtools host and
the Form-specific panel:

```sh
npm install --save-dev @tanstack/react-devtools
npm install --save-dev @tanstack/react-form-devtools@0.2.34
```

The two packages have separate releases. Preserve the versions selected by the
application lockfile.

## Prerequisites and project creation

The docs assume an existing application in React, Preact, Vue, Angular, Solid,
Lit, or Svelte. They do not define a universal project generator, runtime
range, entry file, or build command.

The exact package command is therefore ready for reuse, but greenfield setup
remains partial until the host framework's generated files and scripts are
captured.

## Stable versus alpha

Most core and adapter packages also publish a `2.0.0-alpha.2` dist-tag. That is
not the stable version documented here. Do not mix v2 alpha APIs, validation
semantics, or examples into the `1.33.5` directory.

## Sources

- https://tanstack.com/form/latest/llms.txt
- https://tanstack.com/form/latest/docs/framework.md
- https://github.com/TanStack/form/tree/%40tanstack%2Fform-core%401.33.5/docs
- https://github.com/TanStack/form/releases/tag/%40tanstack%2Fform-core%401.33.5

## Gaps

The installation page lists meta-framework packages, but complete setup is
concentrated in React's SSR guide. Framework-specific runtime requirements and
verification commands are not centralized.
