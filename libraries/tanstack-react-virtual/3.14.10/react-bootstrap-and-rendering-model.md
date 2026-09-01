---
library: "@tanstack/react-virtual"
version: "3.14.10"
topic: "React bootstrap and rendering model"
source: "https://github.com/TanStack/virtual/blob/e9874f033c74afd3251eeb9f3e60b2530cc7ae88/docs/framework/react/react-virtual.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.10; docs at @tanstack/virtual-core@3.17.8 (e9874f033c74afd3251eeb9f3e60b2530cc7ae88)"
---

# React bootstrap and rendering model

The React adapter's element virtualizer is the shortest path to a working
list. The application still owns markup, CSS, measurement policy, and item
content.

## Minimal component

```tsx
import * as React from 'react'
import { useVirtualizer } from '@tanstack/react-virtual'

export function VirtualList({ rows }: { rows: string[] }) {
  const parentRef = React.useRef<HTMLDivElement>(null)

  const virtualizer = useVirtualizer({
    count: rows.length,
    getScrollElement: () => parentRef.current,
    estimateSize: () => 36,
    overscan: 5,
  })

  return (
    <div ref={parentRef} style={{ height: 400, overflow: 'auto' }}>
      <div
        style={{
          height: virtualizer.getTotalSize(),
          width: '100%',
          position: 'relative',
        }}
      >
        {virtualizer.getVirtualItems().map((item) => (
          <div
            key={item.key}
            style={{
              position: 'absolute',
              top: 0,
              left: 0,
              width: '100%',
              height: item.size,
              transform: `translateY(${item.start}px)`,
            }}
          >
            {rows[item.index]}
          </div>
        ))}
      </div>
    </div>
  )
}
```

This is a fixed-estimate bootstrap. Dynamic measurement needs the exact wiring
from a retained dynamic example before that task can be marked ready.

## Required relationships

- `count` is the number of logical items, not the number rendered.
- `getScrollElement` returns the element whose scroll offset is observed.
- `estimateSize` supplies an initial size for every item.
- `getTotalSize()` sizes the inner container for all logical items.
- `getVirtualItems()` returns the visible and overscan window.
- Each virtual item is placed at its `start` offset.

If the scroll element has no bounded height or overflow, the browser may grow
the element instead of scrolling, and virtualization will not reduce visible
layout work as expected.

## Keys and data changes

Use a stable item key when inserts, removals, or reordering occur. The default
index key can be insufficient for preserving measurements and component state
across data changes. Configure the documented key callback when domain IDs are
available.

## Dynamic measurement

When actual sizes differ from estimates, attach the virtualizer's measurement
callback or documented measurement attribute to rendered elements. Estimates
still matter because they shape initial total size and scroll calculations.

Avoid smooth scrolling with dynamically measured items unless the current API
documents a compatible strategy; measurements can change target offsets while
the animation is running.

## Verification

The official docs do not prescribe a build command. In the host React project,
verify that:

1. The scroll container remains 400 pixels high.
2. Its inner size approximates all rows.
3. The DOM contains only the visible window plus overscan.
4. Scrolling reaches the final row.
5. Dynamic content does not leave overlaps or gaps.

Use the host project's real test and build scripts. The example alone does not
prove accessibility, focus retention, or acceptable performance.

## Sources

- https://github.com/TanStack/virtual/blob/e9874f033c74afd3251eeb9f3e60b2530cc7ae88/docs/framework/react/examples/fixed.md
- https://github.com/TanStack/virtual/blob/e9874f033c74afd3251eeb9f3e60b2530cc7ae88/docs/framework/react/examples/dynamic.md
- https://github.com/TanStack/virtual/blob/e9874f033c74afd3251eeb9f3e60b2530cc7ae88/docs/api/virtualizer.md

## Gaps

No first-party page combines project creation, this component, stylesheet or
entry files, and an observable development/build command into one bootstrap
chain.
