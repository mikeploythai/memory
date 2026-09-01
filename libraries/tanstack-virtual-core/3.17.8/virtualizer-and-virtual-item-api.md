---
library: "@tanstack/virtual-core"
version: "3.17.8"
topic: "Virtualizer and VirtualItem API"
source: "https://github.com/TanStack/virtual/blob/e9874f033c74afd3251eeb9f3e60b2530cc7ae88/docs/api/virtualizer.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/virtual-core@3.17.8 (e9874f033c74afd3251eeb9f3e60b2530cc7ae88)"
---

# Virtualizer and VirtualItem API

`Virtualizer` owns measurement, range calculation, scroll observation, and
imperative scrolling. `VirtualItem` describes one logical item selected for the
current rendered range.

## Required options

The central options are:

| Option | Purpose |
|---|---|
| `count` | Number of logical items |
| `getScrollElement` | Resolve the observed scrolling element |
| `estimateSize` | Estimate item size before measurement |

Framework adapters may supply observer and scrolling functions automatically.
Core consumers must configure the documented environment functions directly.

## Common options

- `horizontal` switches the primary axis.
- `overscan` adds items before and after the visible range.
- `getItemKey` supplies stable logical identity.
- `measureElement` customizes actual element measurement.
- `rangeExtractor` can add sticky or otherwise forced items.
- `lanes` supports multi-lane layouts.
- `paddingStart`, `paddingEnd`, and scroll-padding options adjust boundaries.
- `initialRect` and `initialOffset` can support initial or server rendering.
- `enabled` controls observation and updates.

Read the exact reference before setting less common observer, margin, gap, or
scroll-adjustment options; their interactions are implementation-sensitive.

## Instance methods

Important instance methods include:

- `getVirtualItems()` for the selected render range;
- `getTotalSize()` for the logical content extent;
- `scrollToIndex()` and `scrollToOffset()` for imperative movement;
- `measure()` to clear measurements and recompute;
- `resizeItem()` or element measurement for known size changes;
- range and measurement accessors used by advanced integrations.

Imperative scrolling should account for alignment, dynamic measurement, and
scroll padding. An index identifies a logical item, not a DOM child position.

## VirtualItem fields

The [VirtualItem reference](https://tanstack.com/virtual/latest/docs/api/virtual-item.md)
documents the item record used for rendering. Its implementation-sensitive
fields include:

| Field | Meaning |
|---|---|
| `key` | Stable render/measurement identity |
| `index` | Logical item index |
| `start` | Start offset on the primary axis |
| `end` | End offset |
| `size` | Estimated or measured size |
| `lane` | Lane assignment for multi-lane layouts |

Use `key` for rendered identity and `index` to read the backing data. Position
the element from `start`; do not recompute offsets by multiplying index and
estimated size when sizes can vary.

## Measurement rules

Estimates should be realistic and conservative enough to reduce scroll jumps.
Measured sizes replace estimates as elements mount. Changes before the current
viewport may require scroll adjustment to keep the visible content anchored.

For dynamic content, connect the documented measurement mechanism to every
element whose actual size matters. Mixing measured and unmeasured items without
a reliable estimate can create gaps or offset drift.

## Observability and performance

Overscan trades more DOM work for fewer blank edges during fast scrolling.
Measure with representative content rather than assuming a fixed value is
optimal. Avoid broad React state updates on every scroll when virtualizer state
already provides the required range.

## Failure modes

- Returning `null` forever from `getScrollElement` prevents observation.
- Omitting a bounded scroll area renders against the wrong layout assumption.
- Unstable keys discard measurements after reorder.
- Positioning from index instead of `start` breaks variable-size lists.
- Smooth scrolling and live measurement can move the target during animation.

## Sources

- https://tanstack.com/virtual/latest/docs/introduction.md
- https://github.com/TanStack/virtual/tree/%40tanstack%2Fvirtual-core%403.17.8/docs/api

## Gaps

The API pages enumerate contracts but provide limited workflow guidance.
Production tuning thresholds and browser-specific behavior require app tests.
