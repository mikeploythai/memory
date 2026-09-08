---
library: "@tanstack/virtual-core"
version: "3.17.8"
topic: "coverage map"
source: "https://tanstack.com/virtual/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/virtual-core@3.17.8 (e9874f033c74afd3251eeb9f3e60b2530cc7ae88)"
---

# TanStack Virtual 3.17.8 coverage map

## Sources

- https://tanstack.com/virtual/latest/llms.txt
- https://tanstack.com/virtual/latest/docs/index.md
- https://github.com/TanStack/virtual/tree/%40tanstack%2Fvirtual-core%403.17.8/docs
- https://github.com/TanStack/virtual/releases/tag/%40tanstack%2Fvirtual-core%403.17.8
- npm `latest` metadata for every package in `packages/*/package.json`

The release tree and moving `main` tree had matching documentation paths at
retrieval. The hosted llms index omitted Lit from Get Started even though its
adapter page exists in the release tree.

## Bootstrap chain

| Requirement | Evidence | Status | Notes |
|---|---|---|---|
| Package choice and prerequisites | [installation](installation-adapters-and-version-matrix.md) | partial | Exact package versions are known; host framework and layout prerequisites are external. |
| Project creation and installation | [installation](installation-adapters-and-version-matrix.md) | partial | Install commands are exact; no project generator is prescribed. |
| Getting started / quick start | [React bootstrap](../../tanstack-react-virtual/3.14.10/react-bootstrap-and-rendering-model.md) | partial | No dedicated quick-start page; the adapter page and fixed example are combined under the React package. |
| Manual setup | [React bootstrap](../../tanstack-react-virtual/3.14.10/react-bootstrap-and-rendering-model.md) | partial | Component and CSS relationships are present; entry files are absent. |
| Core configuration and mental model | [API](virtualizer-and-virtual-item-api.md) | ready | Count, scroll element, estimate, range, size, and placement are covered. |
| Minimal runnable example | [React bootstrap](../../tanstack-react-virtual/3.14.10/react-bootstrap-and-rendering-model.md) | partial | Component is present; host app and scripts are external. |
| Verification / build | [React bootstrap](../../tanstack-react-virtual/3.14.10/react-bootstrap-and-rendering-model.md) | partial | Observable checks are stated; official command is absent. |
| Common setup mistakes | [API](virtualizer-and-virtual-item-api.md) | ready | Scroll bounds, keys, positioning, measurement, and smooth scrolling are covered. |

Greenfield setup is **partial**. The official corpus does not provide one
complete project with creation, files, scripts, and verification.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Basic React element virtualization | partial | [installation](installation-adapters-and-version-matrix.md), [React bootstrap](../../tanstack-react-virtual/3.14.10/react-bootstrap-and-rendering-model.md) |
| Core API orientation | partial | [Virtualizer and VirtualItem](virtualizer-and-virtual-item-api.md) maps the object model; exact implementation-sensitive signatures and options remain deferred |
| Dynamic/window/grid/chat implementation | partial | [advanced patterns](dynamic-window-grid-chat-and-ssr-patterns.md) |
| Debugging | partial | Failure modes are indexed; no dedicated troubleshooting guide exists. |
| Migration | blocked | No first-party migration section is present. |
| SSR | partial for Marko, blocked generically | Marko examples exist; no cross-framework contract exists. |
| Production/build concerns | partial | Performance tradeoffs are covered; host build and benchmarks are external. |

## Substantive section map

| Source section | Memory page or status |
|---|---|
| Introduction and installation | [installation](installation-adapters-and-version-matrix.md) |
| Framework adapter pages | [React indexed under its package](../../tanstack-react-virtual/3.14.10/react-bootstrap-and-rendering-model.md); adapter version map retained; other adapter pages deferred |
| Pretext | summarized in [advanced patterns](dynamic-window-grid-chat-and-ssr-patterns.md) |
| Chat guide | [advanced patterns](dynamic-window-grid-chat-and-ssr-patterns.md) |
| Virtualizer API | [API](virtualizer-and-virtual-item-api.md) |
| VirtualItem API | [API](virtualizer-and-virtual-item-api.md) |
| Fixed, variable, dynamic examples | fixed/dynamic summarized; complete corpus deferred |
| Padding, sticky, smooth-scroll examples | discovered; deferred |
| Infinite-scroll and table examples | infinite pattern indexed; table detail deferred |
| Window and grid examples | [advanced patterns](dynamic-window-grid-chat-and-ssr-patterns.md) |
| Marko SSR examples | [advanced patterns](dynamic-window-grid-chat-and-ssr-patterns.md) |
| Migration | not present |

## Recipes, warnings, and troubleshooting

| Category | Coverage |
|---|---|
| Fixed element virtualization | indexed |
| Dynamic measurement | partial; behavior and cautions are indexed, but exact React measurement wiring is deferred |
| Stable keys and data reorder | indexed |
| Window virtualization | indexed at pattern level |
| Grid and lanes | indexed at pattern level |
| Infinite loading | indexed at pattern level |
| Chat anchoring and prepend behavior | indexed |
| SSR | Marko-only evidence indexed |
| Dedicated troubleshooting | not present |
| Performance thresholds | not present; representative benchmarks required |

## Version and package mismatches

- Core is `3.17.8`; React is `3.14.10`.
- Solid and Lit are `3.13.37`; Vue and Svelte are `3.13.36`.
- Marko is `3.15.1`; Angular is `6.0.3`.
- Example manifests may pin older Table or adapter versions.
- Lit's adapter page is absent from the llms Get Started list.

## Bounded stopping point

This core batch indexes package selection, the two core API pages, and
advanced-pattern routing. The React rendering bootstrap lives under
`@tanstack/react-virtual@3.14.10`. Complete adapter apps, all 58 example bodies,
sticky/padding recipes, cross-browser benchmarks, and non-Marko SSR validation
are deferred. The catalog contains this coverage map and each substantive page
retained in the batch.

