---
library: "@tanstack/virtual-core"
version: "3.17.8"
topic: "dynamic window grid chat and SSR patterns"
source: "https://github.com/TanStack/virtual/blob/e9874f033c74afd3251eeb9f3e60b2530cc7ae88/docs/chat.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/virtual-core@3.17.8 (e9874f033c74afd3251eeb9f3e60b2530cc7ae88)"
---

# Dynamic, window, grid, chat, and SSR patterns

The official Virtual documentation puts most advanced workflows in examples.
Treat each example as a versioned recipe with its package manifest, not as a
framework-neutral promise.

## Dynamic-size lists

Use realistic estimates and measure rendered elements. Position items from the
virtualizer's `start` offset. When content changes size after rendering, ensure
the element is measured again through the documented adapter mechanism.

Relevant examples:

- https://tanstack.com/virtual/latest/docs/framework/react/examples/dynamic.md
- https://tanstack.com/virtual/latest/docs/framework/vue/examples/dynamic.md
- https://tanstack.com/virtual/latest/docs/framework/svelte/examples/dynamic.md

## Window virtualization

Window virtualizers observe document scrolling rather than a nested element.
Account for the list's offset within the document and any header or scroll
padding. A nested-element recipe cannot be copied unchanged into a window
virtualizer.

- https://tanstack.com/virtual/latest/docs/framework/react/examples/window.md
- https://tanstack.com/virtual/latest/docs/framework/marko/examples/window.md

## Grids and lanes

Multi-column layouts require lane-aware placement. The Marko grid example is
the only grid-labeled example in the llms corpus. The core `lanes` option and
each `VirtualItem.lane` value are the primary API concepts.

- https://tanstack.com/virtual/latest/docs/framework/marko/examples/grid.md

Do not model a variable two-dimensional grid as a fixed one-dimensional list
without checking measurement and lane ordering.

## Infinite scrolling

The examples reserve or detect a loader row near the end of the logical range,
then request more data as that range becomes visible. Guard against duplicate
requests and distinguish loaded row count from total available count.

- https://tanstack.com/virtual/latest/docs/framework/react/examples/infinite-scroll.md
- https://tanstack.com/virtual/latest/docs/framework/angular/examples/infinite-scroll.md
- https://tanstack.com/virtual/latest/docs/framework/vue/examples/infinite-scroll.md

Fetching, caching, retries, and cancellation belong to the data layer, not
TanStack Virtual.

## Chat anchoring

Chat lists need different behavior from ordinary lists:

- follow new content only when the reader was already near the bottom;
- preserve the reader's anchor when older messages are prepended;
- remeasure streaming messages as their content grows;
- avoid forcing the reader to the bottom after manual upward scrolling.

The dedicated [chat guide](https://tanstack.com/virtual/latest/docs/chat.md)
and framework chat examples are the first-party sources:

- https://tanstack.com/virtual/latest/docs/framework/react/examples/chat.md
- https://tanstack.com/virtual/latest/docs/framework/marko/examples/chat.md
- https://tanstack.com/virtual/latest/docs/framework/marko/examples/chat-pretext.md

## Text measurement with Pretext

Pretext provides text measurement for examples where content dimensions can be
predicted before DOM layout. It is optional and separately documented:

- https://tanstack.com/virtual/latest/docs/pretext.md
- https://tanstack.com/virtual/latest/docs/framework/react/examples/pretext.md

Do not treat estimated text metrics as proof of final browser layout when
fonts, width, or rendering conditions differ.

## SSR patterns

The indexed SSR examples are Marko-specific. They cover client-rendered rows
without a server fetch, server-fetched data rendered on the client, server
slices, restored offsets, and window SSR.

- https://tanstack.com/virtual/latest/docs/framework/marko/examples/ssr.md
- https://tanstack.com/virtual/latest/docs/framework/marko/examples/ssr-fetch.md
- https://tanstack.com/virtual/latest/docs/framework/marko/examples/ssr-slice.md
- https://tanstack.com/virtual/latest/docs/framework/marko/examples/ssr-restore.md
- https://tanstack.com/virtual/latest/docs/framework/marko/examples/window-ssr-slice.md

These examples do not establish a generic React, Vue, Angular, or Svelte SSR
contract. Initial rectangle, offset, hydration, and measurement behavior must
be validated in the chosen framework.

## Gaps

There are no dedicated conceptual guides for grids, infinite loading, window
virtualization, or cross-framework SSR. Most evidence is executable example
code, and package manifests must be retained to preserve version context.

## Sources

- https://tanstack.com/virtual/latest/llms.txt
- https://tanstack.com/virtual/latest/docs/api/virtualizer.md
