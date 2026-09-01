---
library: "@tanstack/react-router"
version: "1.170.32"
topic: "router testing and debugging"
source: "https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to/setup-testing.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-router@1.170.32 / a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2"
---

# Router testing and debugging

Router tests should create an isolated router and memory history for each test. Supply the smallest route tree needed for the behavior, navigate to the initial entry, and render through the Router provider. Reusing a global router leaks history, cache, matches, and loader state between tests.

For file-based routes, test the generated behavior rather than editing `routeTree.gen.ts`. Generator tests can run against a controlled fixture and assert the produced route IDs or URLs. Application tests should usually import the generated tree created by the normal build step. If route files were renamed and types or matches look stale, regenerate before investigating runtime code.

Await navigation and loader settlement before asserting rendered output. A route can pass through pending, error, redirect, or not-found states; an assertion made immediately after a click may observe the previous match. Mock data at the loader's dependency boundary and keep params, search validation, and context realistic enough to exercise the route contract.

Debug route identity first. Confirm the generated tree, route ID, pathname, params, and validated search state. Then inspect `beforeLoad`, loader dependencies, cache freshness, and error boundaries. Router Devtools and router events can reveal the active match branch and lifecycle. A component-level symptom is often caused by a route definition or stale generated tree upstream.

Common test mistakes include using browser history in a non-browser environment, failing to provide router context, omitting required search validation, and asserting on raw URLs assembled outside typed navigation. Test redirects and blocked navigation explicitly, including the resulting history entry behavior.

## Sources

- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to/setup-testing.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to/test-file-based-routing.md
- https://github.com/TanStack/router/blob/a5a5bacc8fdf30b7823caf0a94908c3e0db27aa2/docs/router/how-to/debug-router-issues.md


