---
library: "@tanstack/react-virtual"
version: "3.14.9"
topic: "virtualize a long React list"
source: "https://tanstack.com/virtual/v3/docs/introduction"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-virtual@3.14.9; moving v3 docs"
---

# Virtualize a long React list

TanStack Virtual is headless. It calculates measurements and visible ranges; application code owns the scrolling element, total-size spacer, item markup, and positioning.

## Installation

```sh
npm install @tanstack/react-virtual
```

The React adapter and `@tanstack/virtual-core` may have different patch versions. Record both from the lockfile for exact implementation work.

## Use a virtualizer

```tsx
import { useRef } from 'react'
import { useVirtualizer } from '@tanstack/react-virtual'

export function Rows() {
  const parentRef = useRef<HTMLDivElement>(null)
  const virtualizer = useVirtualizer({
    count: 10_000,
    getScrollElement: () => parentRef.current,
    estimateSize: () => 35,
  })

  return (
    <div ref={parentRef} style={{ height: 400, overflow: 'auto' }}>
      <div style={{ height: virtualizer.getTotalSize(), position: 'relative' }}>
        {virtualizer.getVirtualItems().map((item) => (
          <div
            key={item.key}
            style={{
              position: 'absolute',
              width: '100%',
              height: item.size,
              transform: `translateY(${item.start}px)`,
            }}
          >
            Row {item.index}
          </div>
        ))}
      </div>
    </div>
  )
}
```

## Notes

- Give `estimateSize` a realistic value to reduce scroll correction.
- Dynamic-height items require measurement handling.
- The scroll container must have constrained dimensions and scrolling enabled.
- The `v3` documentation is major-versioned but moves as v3 changes.

## Sources

- https://tanstack.com/virtual/latest/docs/installation
- https://tanstack.com/virtual/latest/docs/framework/react
- https://github.com/TanStack/virtual/releases
