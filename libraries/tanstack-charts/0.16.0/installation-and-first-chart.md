---
library: "@tanstack/charts"
version: "0.16.0"
topic: "installation and first chart"
source: "https://github.com/TanStack/charts/blob/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/docs/installation.md"
retrieved_at: "2026-08-31"
source_ref: "258ed39382b09843f98e6f48a2e9d4d0bd3f1d41"
---

# Install TanStack Charts and define a first chart

TanStack Charts `0.16.0` is an alpha TypeScript visualization grammar. New
applications install the unified `@tanstack/charts` package and import exact
subpaths for scales, framework bindings, renderers, and optional capabilities.

## Stability and version contract

The project publishes ordinary `0.x` versions on npm's `latest` tag. Minor
releases may contain breaking API changes while the major remains zero. Pin an
exact version for production evaluation and test each upgrade.

All public Charts packages are an explicitly documented fixed release group.
The following versions were checked independently rather than inferred:

| Package group | Version |
|---|---:|
| `@tanstack/charts` and `@tanstack/charts-scales` | `0.16.0` |
| React, React Native, Preact, Vue, Solid, Svelte adapters | `0.16.0` |
| Angular, Lit, Alpine, and Octane adapters | `0.16.0` |

## Install the unified package

The release README directs new applications to install `@tanstack/charts`
once. With pnpm:

```sh
pnpm add @tanstack/charts
```

Equivalent package-manager syntax may be used, but this page does not invent
unverified project-creation or peer-install commands.

Earlier releases and cached pages may show separate adapter packages such as
`@tanstack/react-charts`. Those packages remain published for compatibility,
but the `0.16.0` release README directs new code to unified subpath imports.

## Verified import boundaries

The release README demonstrates these public boundaries:

```ts
import { barY, defineChart } from '@tanstack/charts'
import { scaleBand } from '@tanstack/charts/scales/band'
import { scaleLinear } from '@tanstack/charts/scales/linear'
import { tooltip } from '@tanstack/charts/tooltip'
import { Chart } from '@tanstack/charts/react'
```

Use exact scale subpaths. The reference states that there is intentionally no
aggregate `@tanstack/charts/scales` export.

## Core authoring sequence

A first chart follows this order:

1. Keep application data in its existing typed row shape.
2. Create the positional scales needed by the chart.
3. Select one or more marks such as `barY` or `lineY`.
4. Call `defineChart()` with the data, marks, channels, scales, and behavior.
5. Render the definition with the selected framework binding or DOM host.
6. Provide an accessible chart name and explicit or responsive sizing.

The definition is framework-independent. Framework bindings own lifecycle and
surface integration, not the visual grammar.

## Package and capability choices

| Need | Import area |
|---|---|
| Common chart definitions and marks | `@tanstack/charts` |
| Compact numeric or categorical scales | `@tanstack/charts/scales/*` |
| React component | `@tanstack/charts/react` |
| Native tooltip behavior | `@tanstack/charts/tooltip` |
| Canvas surface | framework `/canvas` entry or Canvas renderer subpath |
| Static SVG or export | SVG and export subpaths |
| Specialized D3 behavior | Granular D3 module or optional Charts capability |

Compact scales cover common mappings. Use direct D3 callables for temporal,
transformed, piecewise, spatial, locale-aware, or other fuller D3 semantics.

## Verification and known gaps

The checked evidence verifies the package version, installation command,
unified import model, and first-chart mental model. This draft does not retain a
complete `package.json`, component filename, full `defineChart()` object, dev
script, build command, or observable rendering result.

Accordingly, this page is **partial** for greenfield setup. Before marking it
ready, retain the complete pinned quick-start chart, its exact host component,
required peer dependencies, and the official run/build verification.

## Common setup mistakes

- Installing a compatibility adapter package because an older page says to do
  so, then mixing it with unified `0.16.0` subpaths.
- Importing an aggregate scales path that does not exist.
- Omitting the accessible name required by the default host.
- Recreating the definition on every framework render when stable identity is
  the intended application update boundary.
- Assuming alpha minor upgrades are nonbreaking.

## Sources

- https://tanstack.com/charts/latest/docs/overview.md
- https://tanstack.com/charts/latest/docs/installation.md
- https://tanstack.com/charts/latest/docs/stability.md
- https://tanstack.com/charts/latest/docs/quick-start.md
- https://tanstack.com/charts/latest/docs/framework/react/quick-start.md
- https://github.com/TanStack/charts/tree/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41
