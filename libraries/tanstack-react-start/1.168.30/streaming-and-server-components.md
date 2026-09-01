---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "streaming server-function data and server components"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/streaming-data-from-server-functions.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Streaming server-function data and server components

Streaming lets a server function deliver values over time instead of buffering the complete result. It is useful for generated text, long-running processing, incremental records, and other outputs where early chunks improve responsiveness. The client must consume the supported streamed value and handle completion, cancellation, and failure after partial output has already rendered.

Treat a stream as a resource with a lifecycle. Propagate cancellation when the consumer navigates away or starts a replacement request. Stop server work when the request signal is aborted. Do not assume an error can replace the HTTP status after headers and chunks have been sent; represent late failures in the stream protocol or consuming UI.

Stream only serializable, client-safe values. Authentication and input validation happen before privileged work begins. Backpressure and bounded buffering matter for fast producers and slow clients. A stream should not accumulate an unbounded result in memory merely to expose it chunk by chunk.

React Server Components are a separate rendering capability. They execute component logic on the server and transmit a component payload, while streaming server functions expose application data through the function transport. Choose RSC when server-owned component composition is the goal; choose a streamed server function when client UI owns rendering and needs incremental data.

Server Components must respect import direction. Client components cannot freely import server-only implementations, and props crossing the boundary must follow the supported serialization model. Database access and secrets remain in server-only code. Do not translate Next.js RSC file conventions into Start; use the exact Start package and guide for this release candidate line.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/streaming-data-from-server-functions.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/guide/server-components.md


