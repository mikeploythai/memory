---
library: "@tanstack/charts"
version: "0.16.0"
topic: "accessible React chart"
source: "https://github.com/TanStack/charts/tree/v0.16.0/docs"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0; alpha"
---

# Define and render an accessible React chart

TanStack Charts 0.16.0 is alpha software. New React applications install `@tanstack/charts` and import the React renderer through the package's `react` subpath.

## Installation

```sh
npm install @tanstack/charts react react-dom
```

## Define and render

```tsx
import { barY, defineChart } from '@tanstack/charts'
import { scaleBand } from '@tanstack/charts/scales/band'
import { scaleLinear } from '@tanstack/charts/scales/linear'
import { Chart } from '@tanstack/charts/react'

const rows = [
  { month: 'Jan', revenue: 42 },
  { month: 'Feb', revenue: 57 },
]

const definition = defineChart({
  marks: [barY(rows, { x: 'month', y: 'revenue' })],
  scales: {
    x: { scale: () => scaleBand().padding(0.18) },
    y: { scale: scaleLinear, nice: true },
  },
})

export function RevenueChart() {
  return <Chart definition={definition} height={320} ariaLabel="Monthly revenue" />
}
```

## Notes

- Alpha minor releases may contain breaking API changes; pin 0.16.0 for reproducible evaluation.
- Both positional scales are required.
- The default React host renders SVG. Other rendering hosts use explicit package subpaths.
- Memoize a complete chart definition when it depends on changing component values.
- The moving `/charts/latest` site follows the main branch and can be newer than this release. Use the pinned release-source docs for implementation against 0.16.0.

## Sources

- https://tanstack.com/charts/latest/docs/installation
- https://tanstack.com/charts/latest/docs/framework/react/quick-start
- https://github.com/TanStack/charts/blob/main/docs/stability.md
