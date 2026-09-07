---
library: "@tanstack/charts"
version: "0.16.0"
topic: "coverage map"
source: "https://tanstack.com/charts/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "258ed39382b09843f98e6f48a2e9d4d0bd3f1d41"
---

# TanStack Charts 0.16.0 coverage map

This bounded draft covers installation and the first-chart model, core grammar,
interaction/rendering concerns, migration, and API routing. It groups examples
and references instead of copying the large live catalog.

## First-party indices and refs inspected

| Source | Result |
|---|---|
| https://tanstack.com/charts/latest/llms.txt | Moving machine index with Get Started, Guides, API, and Examples sections |
| https://tanstack.com/charts/latest/docs/index.md | Markdown docs index equivalent |
| https://github.com/TanStack/charts/releases/tag/v0.16.0 | Published release record |
| https://github.com/TanStack/charts/tree/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41 | Immutable release source |
| Release `docs/` tree | 102 Markdown pages |
| Package manifests plus npm `latest` | 12 public package versions checked; all were `0.16.0` |

The repository includes root and package-level `llms.txt` files. No hosted
`llms-full.txt` endpoint was present.

## Bootstrap chain

| Requirement | Evidence in this batch | Status |
|---|---|---|
| Package choice and prerequisites | [`installation-and-first-chart.md`](installation-and-first-chart.md) records unified package and alpha policy | partial |
| Installation or project creation | Verified `pnpm add @tanstack/charts` command | partial |
| Required files, peers, and configuration | Import boundaries recorded; exact project files and peer setup not retained | blocked |
| Getting started and mental model | Authoring sequence and ownership model recorded | partial |
| Manual setup/build from scratch | No separate manual-build page found | not applicable |
| Minimal runnable application | Imports are verified, but a complete `defineChart()` and host component are not retained | blocked |
| Verification/build command | Exact script and observable output were not verified | blocked |
| Setup mistakes and version caveats | Unified-package conflict, alpha policy, scale subpaths, and accessibility recorded | ready |

Greenfield setup is not ready because the minimal application and verification
rows remain blocked.

## Task readiness

| Task | Status | Evidence |
|---|---|---|
| Greenfield setup | blocked | Incomplete executable first-chart chain |
| Common feature work | partial | Grammar and interaction pages cover common decisions without complete recipes |
| Debugging | partial | Failure modes and testing checklist indexed; exact diagnostics deferred |
| Migration | partial | [`migration-and-api-map.md`](migration-and-api-map.md); source-version pages absent |
| Production/build concerns | partial | Accessibility, SSR, export, performance, and alpha policy mapped |

## Substantive source-section mapping

| Source section | Status | Indexed page or reason |
|---|---|---|
| Overview, installation, stability | indexed | [`installation-and-first-chart.md`](installation-and-first-chart.md) |
| Generic quick start | partial | Mental model retained; complete app and run command deferred |
| React quick start | partial | Unified import boundary retained; full component deferred |
| Octane quick start | deferred | Requires adapter-specific page |
| Other framework adapters | deferred | Adapter and component pages need package-focused batches |
| Grammar and definitions | partial | [`grammar-definitions-scales-and-marks.md`](grammar-definitions-scales-and-marks.md) covers the model and API boundaries; a complete `defineChart()` definition is deferred |
| Data, channels, scales, marks, layout | indexed at overview level | Same page; exact signatures route to reference |
| Responsive charts and themes | partial | Runtime considerations retained; focused recipes deferred |
| Accessibility and focus | indexed at overview level | [`interaction-rendering-accessibility-and-performance.md`](interaction-rendering-accessibility-and-performance.md) |
| Dynamic data, transforms, animation | partial | Identity and motion rules retained; complete recipes deferred |
| Tooltips, interaction, selection | indexed at overview level | Interaction page |
| Facets, legends, and composition | partial | Routed through grammar/reference; examples deferred |
| Custom marks and renderers | partial | Extension boundary retained; implementation deferred |
| Large data and bundle size | indexed at decision level | Interaction/performance page |
| SSR, hydration, and export | indexed at overview level | Interaction/rendering page |
| TypeScript and testing | partial | Key identity and checklist retained; diagnostics deferred |
| AI authoring | deferred | Agent-specific validation workflow not retained |
| Migration | indexed as route map | [`migration-and-api-map.md`](migration-and-api-map.md) |
| Core API reference | indexed as route map | Same page |
| Mark references | indexed as grouped route map | Same page |
| Framework references | partial | Existing sections named; component signatures deferred |
| Example-family guides | deferred | Fifteen families inventoried but not copied |
| Live chart catalog | deferred | Large executable catalog remains a discovery source |

## Recipes, patterns, and warnings

| Category | Coverage |
|---|---|
| Recipes | Package selection, import boundaries, and chart-authoring sequence |
| Reusable patterns | Stable definitions and keys, layered marks, controlled interaction, renderer-neutral scene |
| Warnings | Exact alpha pinning, accessible names, stable IDs, browser-only export requirements |
| Anti-patterns | Aggregate scales import, index keys for mutable data, automatic compatibility-package rewrites |
| Troubleshooting | Testing checklist and failure modes; no standalone troubleshooting page found |
| Migrations | Broad guide and release-note workflow; no per-minor matrix |
| API | 37 reference pages mapped by area plus framework and mark groups |

## Version and package mismatches

- The fixed `0.16.0` release group was confirmed from the stability contract,
  repository manifests, and npm metadata; it was not inferred.
- Compatibility adapter packages remain published, while the release README
  directs new applications to unified `@tanstack/charts` subpaths.
- Cached older documentation can show separate adapter installation commands.
- `@tanstack/react-native-charts@0.16.0` has no matching release documentation
  section.

## Meaningful gaps

- No hosted `llms-full.txt`.
- No complete executable chart and run/build verification in this batch.
- Only React and Octane have dedicated quick starts.
- No React Native framework docs despite a published package.
- No release-to-release alpha migration matrix or verified codemod.
- The live catalog is too large for this bounded five-page batch.

## Bounded stopping point

This batch stops after five `@tanstack/charts@0.16.0` pages. The next batch
should complete and verify the immutable React first-chart bootstrap before
adding adapter-specific pages or example families. Keep greenfield readiness
blocked until that executable chain passes using Memory alone.

## Sources

- https://tanstack.com/charts/latest/llms.txt
- https://github.com/TanStack/charts/tree/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/docs
- https://github.com/TanStack/charts/tree/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/packages

