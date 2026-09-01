---
library: "@tanstack/form-core"
version: "1.33.5"
topic: "coverage map"
source: "https://tanstack.com/form/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/form-core@1.33.5 (b865ef335a69aa08a2f160895258f13e03773467)"
---

# TanStack Form 1.33.5 coverage map

## First-party sources inspected

- https://tanstack.com/form/latest/llms.txt
- https://tanstack.com/form/latest/docs/index.md
- https://github.com/TanStack/form/tree/%40tanstack%2Fform-core%401.33.5/docs
- https://github.com/TanStack/form/releases/tag/%40tanstack%2Fform-core%401.33.5
- npm `latest` metadata for every package in `packages/*/package.json`

The pinned release and moving `main` tree had matching documentation paths at
retrieval. V2 alpha releases exist but are excluded from this stable-v1 map.

## Bootstrap chain

| Requirement | Evidence | Status | Notes |
|---|---|---|---|
| Package choice and prerequisites | [installation](installation-adapters-and-version-matrix.md) | partial | Exact package matrix is known; framework/runtime prerequisites are external. |
| Project creation and installation | [installation](installation-adapters-and-version-matrix.md) | partial | Install commands are exact; no project generator is prescribed. |
| Getting started / quick start | [React quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md) | partial | A basic React form lifecycle is retained, but the host app is external and other adapters need their own pages. |
| Manual setup | [React quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md) | partial | Existing React app is assumed. |
| Core configuration and mental model | [core API map](core-api-and-framework-gaps.md), [React quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md) | partial | The retained React example illustrates values, fields, subscriptions, and submission; it is not a complete core implementation reference. |
| Minimal runnable example | [React quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md) | partial | Component is present; host entry file and scripts are external. |
| Verification / build | [React quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md) | partial | Observable behavior is stated; official command is absent. |
| Common setup mistakes | [React validation](../../tanstack-react-form/1.33.5/validation-submission-and-composition.md) | partial | Several React failure modes are retained, but arrays, async initial values, server errors, and cross-framework troubleshooting are deferred. |

Greenfield setup is **partial** because the official chain starts inside an
existing framework application.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Basic React form and retained validation patterns | partial | [React quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md), [React validation](../../tanstack-react-form/1.33.5/validation-submission-and-composition.md); broader feature contracts remain deferred. |
| Other adapter implementation | partial | Package and guide map exists; adapter-specific code is deferred. |
| Debugging | partial | Failure modes and React/Preact guides are mapped; no common error catalog exists. |
| Stable v1 migration | blocked | No dedicated first-party migration section was found. |
| V2 alpha migration | not applicable | Alpha is outside this stable version directory. |
| Production/build concerns | partial | SSR and submission concerns are mapped; host build remains external. |

## Substantive section map

| Source section | Memory page or status |
|---|---|
| Overview, philosophy, comparison, TypeScript | Core package choices in [installation](installation-adapters-and-version-matrix.md); selected React concepts in the [adapter quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md) |
| Installation and framework selection | [installation](installation-adapters-and-version-matrix.md) |
| Seven framework quick starts | React indexed; six adapter pages deferred |
| Basic concepts and reactivity | React subset in the [adapter quick start](../../tanstack-react-form/1.33.5/react-quick-start-and-basic-concepts.md) |
| Validation and dynamic validation | React subset in [adapter validation](../../tanstack-react-form/1.33.5/validation-submission-and-composition.md) |
| Async values, arrays, groups, linked fields | mapped; detailed recipes deferred |
| Submission and custom errors | React subset in [adapter validation](../../tanstack-react-form/1.33.5/validation-submission-and-composition.md) |
| Composition and UI libraries | composition indexed; UI integrations deferred |
| Focus management and accessibility | warnings indexed; complete recipe not present |
| React Native and SSR | discovered; deferred |
| Debugging and devtools | discovered; deferred |
| Core and adapter API | [API map](core-api-and-framework-gaps.md) |
| Migration | not present |
| 39 examples | discovered; not copied in this batch |

## Recipes, warnings, and troubleshooting

| Category | Coverage |
|---|---|
| Default values and typed field paths | indexed |
| Granular subscriptions | indexed |
| Sync, async, dynamic, and schema validation | indexed |
| Submission lifecycle | indexed |
| Form composition | indexed at pattern level |
| Arrays and async initial values | deferred |
| Server error protocol | not specified by library |
| Cross-framework troubleshooting | not present |
| Migration recipes | not present |

## Version and package mismatches

- Core and most adapters are `1.33.5`.
- Preact is `1.30.5`; Lit is `1.25.5`.
- Devtools packages are `0.2.34`.
- Most packages expose `2.0.0-alpha.2`, which is intentionally excluded.
- Svelte has no generated adapter reference; Lit has only three pages.

## Bounded stopping point

This core batch indexes stable-v1 package selection and the API/framework gap
map. React bootstrap, validation, submission, and composition live under
`@tanstack/react-form@1.33.5` and remain partial beyond the retained examples.
Complete non-React adapters, arrays, SSR, React Native, devtools operation,
example projects, and alpha documentation are deferred. No catalog entry is
created.
