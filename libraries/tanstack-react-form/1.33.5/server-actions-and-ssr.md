---
library: "@tanstack/react-form"
version: "1.33.5"
topic: "server actions and SSR"
source: "https://github.com/TanStack/form/blob/b865ef335a69aa08a2f160895258f13e03773467/docs/framework/react/guides/ssr.md"
retrieved_at: "2026-08-31"
source_ref: "b865ef335a69aa08a2f160895258f13e03773467"
---

# Server actions and SSR

TanStack Form provides separate adapters for TanStack Start, Next.js, and Remix integration. Share a typed `formOptions` definition between client and server so both sides agree on the value shape and validation contract. The server remains authoritative even when equivalent client validation improves feedback.

In TanStack Start, a server function validates and handles the submission, while server-returned form state can be read by a loader and merged into the client form. In Next.js App Router, a Server Action handles the native form post and React action state is transformed into form state. In Remix, the route action returns validation state consumed through action data.

Native form posts require every control to have a `name` attribute. TanStack Form's typed field name is the correct source. Omitting the DOM name can make a field appear correct in client state while disappearing from `FormData` on the server.

Import the environment-specific adapter. Next.js server code belongs in `@tanstack/react-form-nextjs`; importing client or generic code into the server graph can produce the documented environment error. The same boundary matters for Start and Remix packages.

Hydration requires deterministic defaults. Do not generate different initial values during server and client rendering. Server validation errors should be serialized through the integration's supported form-state format, not by sending Error objects or executable code. Treat all returned values as untrusted request data and validate again before performing domain actions.

## Sources

- [React meta-framework guide](https://tanstack.com/form/latest/docs/framework/react/guides/ssr.md)
- [TanStack Start example](https://tanstack.com/form/latest/docs/framework/react/examples/tanstack-start.md)
- [Next server-actions example](https://tanstack.com/form/latest/docs/framework/react/examples/next-server-actions.md)
- [Remix example](https://tanstack.com/form/latest/docs/framework/react/examples/remix.md)


