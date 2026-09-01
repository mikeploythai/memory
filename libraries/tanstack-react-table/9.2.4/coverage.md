---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "documentation coverage map"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/overview.md"
retrieved_at: "2026-08-31"
source_ref: "d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6"
---

# TanStack React Table documentation coverage

This batch indexes the React-facing concepts most likely to affect implementation correctness. The official `llms.txt` remains the routing index for every generated page. GitHub commit `d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6` is the immutable source boundary for `@tanstack/react-table` 9.2.4.

## Indexed in this batch

- Setup, quick start, v8-to-v9 migration, and the legacy bridge.
- Feature registration, tree shaking, row models, and function registries.
- Data and column typing, identity stability, table state, atoms, selectors, React Compiler behavior, and rendering primitives.
- Client/server processing, remote sorting and pagination, filtering, faceting, grouping, aggregation, expansion, selection, pinning, column layout, and virtualization.
- Core and React API routing plus custom plugins and composable table hooks.

## Deferred but present upstream

- Individual generated API pages for every symbol. The two indexed API maps link to them; copy a symbol page only when a task needs its exact signature.
- Every runnable example. High-value remote-data and virtualization examples are linked from topic pages. Component-library variants, DnD, spreadsheet, realtime-trading, and kitchen-sink examples remain in `llms.txt`.
- Devtools and TanStack Intent agent-skill pages.
- Non-React adapters: Alpine, Angular, Ember, Lit, Octane, Preact, Solid, Svelte, Vue, and vanilla.
- Experimental worker and imperative virtualization implementations beyond their constraints and routing links.

## Not present as dedicated upstream sections

There is no standalone “anti-patterns” manual. Documented failure modes are distributed through the data, state, client/server, compiler, feature, and virtualization guides and have been retained in the corresponding topic pages. There is also no built-in fetching or server row-model layer; those responsibilities are explicitly external.

## Stopping point

The batch stops at twelve topic pages plus this map. It does not mirror hundreds of generated symbols or every framework/example variant. Future retrieval should consult `llms.txt`, choose the smallest relevant Markdown page, and add a new topic only when the current pages and API maps do not answer the implementation question.

## Sources

- [Official Table llms.txt](https://tanstack.com/table/latest/llms.txt)
- [Immutable documentation tree](https://github.com/TanStack/table/tree/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs)

