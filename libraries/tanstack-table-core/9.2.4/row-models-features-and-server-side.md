---
library: "@tanstack/table-core"
version: "9.2.4"
topic: "row models features and server-side processing"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/row-models.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/table-core@9.2.4 (d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6)"
---

# Row models, features, and server-side processing

Row models are staged transformations of the original data. V9 includes the
core row model automatically. Register only the optional feature objects and
row-model slots the application uses. Unregistered or manual stages pass the
previous row model through instead of processing it locally.

## Processing pipeline

The documented order is:

1. core rows from input data;
2. filtering and faceting;
3. grouping and aggregation;
4. sorting;
5. expansion;
6. pagination.

A core-focused client-side feature definition registers each optional row model
as a slot on `tableFeatures`, together with its corresponding feature object:

```ts
import {
  columnFilteringFeature,
  createFilteredRowModel,
  createPaginatedRowModel,
  createSortedRowModel,
  rowPaginationFeature,
  rowSortingFeature,
  tableFeatures,
} from '@tanstack/table-core'

const features = tableFeatures({
  columnFilteringFeature,
  rowSortingFeature,
  rowPaginationFeature,
  filteredRowModel: createFilteredRowModel(),
  sortedRowModel: createSortedRowModel(),
  paginatedRowModel: createPaginatedRowModel(),
})
```

Pass `features`, `data`, and `columns` to the selected framework adapter. The
core row model is part of every v9 table automatically and needs no application
configuration.

## Client-side versus server-side

Client-side processing is appropriate when the browser can hold the relevant
rows and compute the required models at acceptable cost. Test with realistic
row shapes and target hardware; row count alone is not a reliable limit.

For server-side filtering, sorting, or pagination:

- omit the corresponding client row-model creator;
- enable the documented `manual*` option for that feature;
- pass already processed rows from the server;
- control the relevant state and include it in the request key;
- supply total row or page information when pagination needs it.

Do not register a client-side stage and also assume the server is authoritative
for that same stage. That can process an already processed subset and produce
incorrect counts or ordering.

## Data and identity

The core never mutates the input data array. Accessors and row-model stages may
derive values represented by row and cell objects.

Provide stable, domain-level row IDs when row selection, expansion, or updates
must survive sorting and pagination. Positional IDs are fragile when the server
reorders or replaces rows.

## Feature groups

The first-party guides cover:

- column and global filtering, faceting, and fuzzy ranking;
- grouping and aggregation;
- sorting and pagination;
- row selection, expansion, and pinning;
- column ordering, visibility, sizing, resizing, and pinning;
- cell selection and spanning;
- custom features and composable table configurations;
- framework-specific virtualization.

Each stateful feature has options, state, change handlers, and instance APIs.
Index feature-specific guides when implementing that feature; this page is the
decision map, not a replacement for those contracts.

## Workers and virtualization

Worker row models can move expensive processing off the main thread, but data
serialization and synchronization become part of the cost model. Benchmark
before adopting them.

Virtualization changes rendering, not the row-model pipeline. TanStack Table
can supply rows to TanStack Virtual, but it does not virtualize rows by itself.
Keep the package versions independent.

## Common failure modes

- New `data` references on every render invalidate all downstream row models.
- Manual server modes without controlled state leave requests out of sync.
- Paginating before grouping or filtering on the server changes visible counts.
- Using array indices as IDs makes selection drift after sorting.
- Rendering every row defeats virtualization even when a virtualizer exists.

## Sources

- https://tanstack.com/table/latest/docs/guide/client-side-vs-server-side.md
- https://tanstack.com/table/latest/docs/guide/features.md
- https://tanstack.com/table/latest/docs/guide/worker-row-models.md
- https://tanstack.com/table/latest/docs/framework/react/guide/virtualization.md
- https://tanstack.com/table/latest/docs/guide/data.md

## Gaps

The official docs provide examples rather than a universal performance
threshold. Server API schemas, cache policy, and accessibility behavior belong
to the application and are not specified by Table.
