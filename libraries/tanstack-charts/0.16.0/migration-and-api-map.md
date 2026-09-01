---
library: "@tanstack/charts"
version: "0.16.0"
topic: "migration and API map"
source: "https://github.com/TanStack/charts/blob/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/docs/guides/migrating.md"
retrieved_at: "2026-08-31"
source_ref: "258ed39382b09843f98e6f48a2e9d4d0bd3f1d41"
---

# TanStack Charts migration and API map

TanStack Charts `0.16.0` is alpha. A migration must start from the exact source
version and should not assume that all `0.x` minors are API compatible.

## Migration sources

The release has one broad migration guide:

- https://tanstack.com/charts/latest/docs/guides/migrating.md

Release notes and `CHANGELOG.md` are required when moving between two specific
minor versions because the guide is not a per-release compatibility matrix.
Keep separate source- and target-version Memory pages for an actual migration.

## Unified-package boundary

The `0.16.0` release README directs new applications to install
`@tanstack/charts` once and use exact subpaths:

```ts
import { scaleLinear } from '@tanstack/charts/scales/linear'
import { Chart } from '@tanstack/charts/react'
import { Chart as CanvasChart } from '@tanstack/charts/react/canvas'
```

Existing framework-specific package names remain published for compatibility.
Do not mechanically rewrite imports until the source package version and target
subpath behavior have been checked.

Historical changes also moved optional tooltip composition to explicit tooltip
entries and renamed some root, Canvas, and renderer-neutral components. Use the
changelog for the exact source release rather than applying an old migration to
`0.16.0` blindly.

## API overview

The release reference is organized into these core areas:

| Area | Reference page |
|---|---|
| Definitions and responsive alternatives | `reference/chart-definitions.md` |
| Lower-level object spec | `reference/chart-spec.md` |
| View composition | `reference/view-composition.md` |
| Data transforms | `reference/transforms.md` |
| Scales, guides, color, and gradients | `reference/scales-guides-and-color.md` |
| Vanilla DOM host | `reference/dom-host.md` |
| Framework lifecycle controller | `reference/adapter-controller.md` |
| Runtime and renderer-neutral scene | `reference/runtime-and-scene.md` |
| Focus and interaction | `reference/focus-and-interaction.md` |
| Rendering and export | `reference/rendering-and-export.md` |
| Motion | `reference/motion.md` |
| Custom extension contracts | `reference/custom-extensions.md` |
| Public generic and scene types | `reference/types.md` |

## Framework references

Component references exist for React, Preact, Vue, Solid, Svelte, Angular, Lit,
Alpine, and Octane. React and Octane additionally have dedicated quick starts.

The repository publishes `@tanstack/react-native-charts@0.16.0`, but the
release documentation tree has no matching React Native framework section.
Treat its package README and declarations as the available exact-version
authority until first-party framework docs are added.

## Mark-reference groups

The API includes focused pages for line/area, difference, regression, bars,
boxes, dots, dodge, waffle, ridgeline, violin, focus guides, hierarchy, Sankey,
hexbin, contours, Delaunay, Voronoi, rules and links, text and facets, geo, and
polar marks.

Use the API overview as the routing page instead of copying all exports into a
single Memory document.

## Migration checklist

1. Record the exact installed source packages and versions.
2. Read every release note between source and `0.16.0`.
3. Identify compatibility-package imports and target unified subpaths.
4. Check definition, scale, tooltip, host, and renderer API changes separately.
5. Type-check the migrated application.
6. Verify SSR/hydration, keyboard interaction, responsive layout, and export.
7. Compare output with representative data rather than a single toy chart.

## Gaps and confidence

- There is no release-to-release migration matrix or codemod documented in the
  bounded source set.
- Alpha minor releases may break public APIs.
- React Native lacks a corresponding documentation section.
- Cached pre-`0.16` pages can conflict with the unified-package release README.

## Sources

- https://tanstack.com/charts/latest/docs/guides/migrating.md
- https://tanstack.com/charts/latest/docs/reference/index.md
- https://tanstack.com/charts/latest/docs/stability.md
- https://github.com/TanStack/charts/blob/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/CHANGELOG.md
- https://github.com/TanStack/charts/tree/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/docs/reference
