---
library: "@tanstack/form-core"
version: "1.33.5"
topic: "core API and framework documentation gaps"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/reference/index.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/form-core@1.33.5 (b865ef335a69aa08a2f160895258f13e03773467)"
---

# Core API and framework documentation gaps

Use hand-written guides to understand workflows and generated references to
verify exact signatures. The API corpus is broader than the 47 links selected
by the official llms index.

## Core classes

| Class | Role |
|---|---|
| `FormApi` | values, validation, submission, state, fields |
| `FieldApi` | one field's value, metadata, handlers, validation |
| `FormGroupApi` | grouped values and group-level behavior |
| `FieldGroupApi` | reusable typed field group behavior |

Reference roots:

- https://tanstack.com/form/latest/docs/reference/classes/FormApi.md
- https://tanstack.com/form/latest/docs/reference/classes/FieldApi.md
- https://tanstack.com/form/latest/docs/reference/classes/FormGroupApi.md
- https://tanstack.com/form/latest/docs/reference/classes/FieldGroupApi.md

## Core functions and types

Important functions include `formOptions`, `mergeForm`, `revalidateLogic`, and
standard-schema detection helpers. Important type areas include:

- `FormOptions`, `FormValidators`, and `FormState`;
- `FieldOptions`, `FieldValidators`, and field metadata;
- deep key/value types for nested field names;
- validation logic, source, metadata, and error types;
- updater functions and derived form state.

Start with the [core reference index](https://tanstack.com/form/latest/docs/reference/index.md)
and retrieve only the exact symbol pages needed for implementation.

## Adapter references

| Framework | Reference root | Relative completeness in pinned tree |
|---|---|---:|
| React | https://tanstack.com/form/latest/docs/framework/react/reference/index.md | 24 pages |
| Preact | https://tanstack.com/form/latest/docs/framework/preact/reference/index.md | 25 pages |
| Vue | https://tanstack.com/form/latest/docs/framework/vue/reference/index.md | 17 pages |
| Solid | https://tanstack.com/form/latest/docs/framework/solid/reference/index.md | 20 pages |
| Angular | https://tanstack.com/form/latest/docs/framework/angular/reference/index.md | 11 pages |
| Lit | https://tanstack.com/form/latest/docs/framework/lit/reference/index.md | 3 pages |
| Svelte | no generated reference root in pinned tree | 0 pages |

The absence of generated Svelte reference pages is a documentation gap, not
evidence that the Svelte package lacks APIs. Inspect the exact package artifact
when signatures matter.

## Guide coverage by framework

React has the broadest set: basic concepts, validation, dynamic validation,
async initial values, arrays, groups, linked fields, reactivity, listeners,
custom errors, submission, UI libraries, focus, composition, React Native,
SSR, debugging, and devtools.

Preact is close but lacks React Native, SSR, and a dedicated devtools page.
Vue, Angular, Solid, Lit, and Svelte document subsets. Do not assume a React
workflow has an equivalent adapter API without checking its guide and package.

## Migrations

The stable v1 docs tree contains no dedicated migration section. There is no
first-party, versioned pre-v1-to-v1 migration chain in the indexed corpus.
Migration readiness is therefore blocked unless release notes or exact package
changelogs are indexed separately.

Form v2 alpha documentation must live under separate package/version paths.
Its current alpha dist-tag does not supersede stable v1.

## Debugging sources

React and Preact have debugging guides; React and Solid have devtools guides.
Useful state checks include field metadata, validation status, submitting
status, and selector scope. The docs do not provide a cross-framework error
catalog.

## Version checks

```sh
npm view @tanstack/form-core version
npm view @tanstack/preact-form version
npm view @tanstack/lit-form version
npm view @tanstack/react-form-devtools version
```

At retrieval these were `1.33.5`, `1.30.5`, `1.25.5`, and `0.2.34`.

## Sources

- https://tanstack.com/form/latest/llms.txt
- https://github.com/TanStack/form/tree/%40tanstack%2Fform-core%401.33.5/docs/reference
- https://github.com/TanStack/form/tree/%40tanstack%2Fform-core%401.33.5/docs/framework
