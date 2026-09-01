---
library: "@tanstack/charts"
version: "0.16.0"
topic: "grammar, definitions, scales, and marks"
source: "https://github.com/TanStack/charts/blob/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/docs/concepts/grammar-of-graphics.md"
retrieved_at: "2026-08-31"
source_ref: "258ed39382b09843f98e6f48a2e9d4d0bd3f1d41"
---

# Grammar, definitions, scales, and marks

TanStack Charts uses a typed grammar of graphics. Data remains application
data; marks consume rows, channels extract values, scales map values into visual
space, and definitions compose the result into a responsive chart runtime.

## Ownership model

| Layer | Owns |
|---|---|
| Application data | Row shape, domain meaning, loading, and updates |
| Mark | Geometric representation of selected rows |
| Channel | Extraction or derivation of visual values from a row |
| Scale | Mapping between a data domain and visual range |
| Guide | Axes, legends, gradients, and labels derived from scales |
| Definition | Marks, scales, layout, theme, behavior, and responsiveness |
| Runtime | Compiled scene, measurement, focus, updates, and rendering |
| Framework adapter | Lifecycle, mounting, hydration, and component props |

## Definitions

`defineChart()` creates the normal authoring boundary. The definition's identity
is also an application update boundary for framework hosts. Keep it stable when
inputs have not changed; create a new definition when chart inputs or behavior
change.

Definitions can own responsive alternatives. The runtime selects the applicable
definition for the measured size, then compiles a renderer-neutral scene.

The separate `ChartSpec` API represents the lower-level object form documented
by the reference. Use the ordinary definition API unless a feature specifically
requires direct spec construction.

## Data and channels

Marks can consume arrays, objects, tuples, and iterables directly. Different
layers may use different datum types. Channels may read properties or use typed
accessor functions.

Stable datum identity matters for focus, selection, reconciliation, and
animation. Do not use an array index as an identity when rows can be inserted,
removed, sorted, or streamed.

Transforms are eager and return data used by marks. Keep transformation policy
explicit when grouping, stacking, binning, reducing, or deriving hierarchy.

## Scale choice

The unified package exposes compact scales through exact subpaths:

```ts
import { scaleBand } from '@tanstack/charts/scales/band'
import { scaleLinear } from '@tanstack/charts/scales/linear'
import { scaleOrdinal } from '@tanstack/charts/scales/ordinal'
import { scalePoint } from '@tanstack/charts/scales/point'
```

Use compact scales for common numeric linear and categorical mappings. Use
granular D3 modules or accepted D3 scale instances when a chart needs time,
logarithmic or other transformed domains, piecewise behavior, specialized
interpolation, or locale-aware functionality.

Do not assume unsupported D3 behavior will warn or fall back at runtime. Select
the full D3 implementation deliberately.

## Mark families

The release reference documents these families:

- line, area, difference, and regression;
- bar, rect, cell, box, dot, hexagon, dodge, waffle, ridgeline, and violin;
- rules, links, arrows, vectors, ticks, text, frames, and facets;
- treemap, sunburst, Sankey, hierarchy trees, and network layouts;
- hexbin, contour, density, Delaunay, and Voronoi;
- geographic shapes, polar marks, radial marks, and polar guides;
- focus guides, crosshairs, and view composition.

Choose a mark from the reader's question and data shape, not from decoration.
Layer marks when separate visual roles share a coordinate system.

## Guides, layout, and coordinates

Positional scales drive axes and layout. Color scales drive legends or gradient
legends. Automatic guide margins are part of the runtime, but long labels,
multiple axes, and compact containers still require an explicit design choice.

Cartesian, polar, geographic, hierarchy, and network views have different
coordinate and layout semantics. Do not force spatial or hierarchical data into
ordinary categorical axes merely to reuse a familiar mark.

## Extension boundary

Custom marks compile into the same public scene protocol as built-in marks.
Custom renderers consume that scene. Reach for these extension points only
after checking whether a built-in mark, transform, view composition, or direct
D3 callable covers the requirement.

## Failure modes

- Using the wrong scale type for the channel domain.
- Letting inferred domains change unexpectedly as streamed data moves.
- Recreating unstable keys and losing meaningful animation.
- Mutating data behind a definition without triggering its documented update
  boundary.
- Importing broad optional capabilities into a bundle that needs one subpath.

## Sources

- https://tanstack.com/charts/latest/docs/concepts/grammar-of-graphics.md
- https://tanstack.com/charts/latest/docs/concepts/chart-definitions.md
- https://tanstack.com/charts/latest/docs/concepts/data-and-channels.md
- https://tanstack.com/charts/latest/docs/concepts/scales-and-d3.md
- https://tanstack.com/charts/latest/docs/concepts/marks-and-layering.md
- https://tanstack.com/charts/latest/docs/concepts/layout-axes-and-coordinates.md
- https://tanstack.com/charts/latest/docs/reference/chart-definitions.md
- https://tanstack.com/charts/latest/docs/reference/scales-guides-and-color.md
