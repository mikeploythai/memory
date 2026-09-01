---
library: "@tanstack/charts"
version: "0.16.0"
topic: "interaction, rendering, accessibility, and performance"
source: "https://github.com/TanStack/charts/blob/258ed39382b09843f98e6f48a2e9d4d0bd3f1d41/docs/guides/interactions-and-selections.md"
retrieved_at: "2026-08-31"
source_ref: "258ed39382b09843f98e6f48a2e9d4d0bd3f1d41"
---

# Interaction, rendering, accessibility, and performance

TanStack Charts keeps interaction policy in the chart definition and host while
renderers paint a shared scene. This allows SVG, Canvas, static output, and
custom renderers to share chart semantics.

## Focus and interaction

The interaction reference covers pointer focus, keyboard navigation, native
tooltips, selection, brushing, continuous cursors, controlled signals, and
horizontal zoom.

The default host requires an accessible chart name. Its documented options
include `ariaLabel`, optional `ariaDescription`, fixed or responsive sizing,
initial responsive width, resource ID prefixes, keyboard tab index, and focus
callbacks.

Keep application-owned state controlled when other components need to share it.
For example, a table and chart can share selection while the chart definition
still owns marks and focus presentation.

## Tooltips

Native tooltips are optional. Grouped focus, formatting, keyboard behavior, and
portal placement are separate choices.

A portaled tooltip may use the browser top layer or a fixed body fallback. This
avoids clipping inside chart containers, but the application must still account
for document ownership, dismissal, and focus behavior.

Do not rely on hover alone. Keyboard users need a focus path to the same data,
and touch interactions need an explicit activation or pinning policy.

## Rendering surfaces

| Surface | Use |
|---|---|
| SVG | Default accessible and server-renderable surface |
| Canvas | Opt-in painting for suitable high-density workloads |
| Static SVG | Server output, snapshots, and noninteractive documents |
| Custom renderer | Application-owned scene painting with shared host behavior |

The renderer-neutral host continues to own sizing, text measurement, focus,
keyboard behavior, tooltips, selection, and callbacks. A custom renderer should
not silently replace these responsibilities.

## Export

The release reference documents static SVG rendering, SVG reconciliation,
serialization, browser image export, and download helpers.

Verified import boundaries include:

```ts
import { renderChartSvg } from '@tanstack/charts/svg'
import { downloadChartSvg, serializeChartSvg } from '@tanstack/charts/export'
```

Raster export requires a browser document and window, nonzero chart dimensions,
Canvas 2D, and successful image decoding. It can produce PNG, JPEG, or WebP.
Keep the filename extension aligned with the chosen MIME type.

Use stable, document-unique `idPrefix` values for gradients, clip paths, and
other renderer-owned resources, especially with SSR or multiple charts.

## Motion and reduced motion

Definition-owned animation defaults to a short ease-out transition and respects
reduced-motion preferences. Stable mark and datum identities are required for
meaningful transitions.

Resize animation is opt-in. Initial rendering does not animate. Interrupted
updates and responsive resizing should be tested with real application data,
not only isolated demos.

## Performance choices

- Import exact subpaths so optional marks, transforms, renderers, and
  interactions remain tree-shakeable.
- Keep definition identity stable when inputs are unchanged.
- Select Canvas only after measuring an SVG workload and accessibility impact.
- Reduce or aggregate dense data when individual marks cannot be perceived.
- Test text measurement and guide layout at the smallest supported container.
- Use the large-data and bundle-size guides before creating a custom renderer.

## SSR and hydration

Use stable IDs and the same definition inputs on server and client. Framework
adapter pages document lifecycle and hydration boundaries. Browser-only
measurement, portals, and raster export must not run as if they were available
during server rendering.

## Testing checklist

1. Verify the accessible name and keyboard navigation.
2. Exercise pointer, touch, and controlled selection behavior.
3. Test narrow and wide responsive layouts.
4. Render with reduced motion enabled.
5. Check SSR output and hydration for stable resource IDs.
6. Test export with real fonts, gradients, and dimensions.
7. Measure bundle and update cost before changing renderers.

## Sources

- https://tanstack.com/charts/latest/docs/guides/accessibility.md
- https://tanstack.com/charts/latest/docs/guides/tooltips-and-focus.md
- https://tanstack.com/charts/latest/docs/guides/interactions-and-selections.md
- https://tanstack.com/charts/latest/docs/guides/large-data.md
- https://tanstack.com/charts/latest/docs/guides/ssr-and-hydration.md
- https://tanstack.com/charts/latest/docs/guides/exporting.md
- https://tanstack.com/charts/latest/docs/guides/bundle-size-and-performance.md
- https://tanstack.com/charts/latest/docs/reference/dom-host.md
- https://tanstack.com/charts/latest/docs/reference/rendering-and-export.md
- https://tanstack.com/charts/latest/docs/reference/motion.md
