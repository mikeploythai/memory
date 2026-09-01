---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "React quick start and table state"
source: "https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/quick-start.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-table@9.2.4 (d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6)"
---

# React quick start and table state

TanStack Table v9 makes features explicit. A React table declares them with
`tableFeatures`, passes that feature set to `useTable`, and renders headers and
cells with `table.FlexRender`. The core row model is included automatically.

## Complete table component

```tsx
import { tableFeatures, useTable } from '@tanstack/react-table'
import type { ColumnDef } from '@tanstack/react-table'

type Person = {
  firstName: string
  lastName: string
  age: number
}

const data: Array<Person> = [
  { firstName: 'Ada', lastName: 'Lovelace', age: 36 },
  { firstName: 'Grace', lastName: 'Hopper', age: 37 },
]

const features = tableFeatures({})

const columns: Array<ColumnDef<typeof features, Person>> = [
  {
    accessorKey: 'firstName',
    header: 'First name',
    cell: (info) => info.getValue(),
  },
  {
    accessorFn: (row) => row.lastName,
    id: 'lastName',
    header: () => <span>Last name</span>,
    cell: (info) => <i>{info.getValue<string>()}</i>,
  },
  {
    accessorKey: 'age',
    header: 'Age',
  },
]

export function PersonTable() {
  const table = useTable({
    features,
    columns,
    data,
  })

  return (
    <table>
      <thead>
        {table.getHeaderGroups().map((headerGroup) => (
          <tr key={headerGroup.id}>
            {headerGroup.headers.map((header) => (
              <th key={header.id}>
                {header.isPlaceholder ? null : (
                  <table.FlexRender header={header} />
                )}
              </th>
            ))}
          </tr>
        ))}
      </thead>
      <tbody>
        {table.getRowModel().rows.map((row) => (
          <tr key={row.id}>
            {row.getAllCells().map((cell) => (
              <td key={cell.id}>
                <table.FlexRender cell={cell} />
              </td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  )
}
```

`tableFeatures({})` selects core features only. V9 supplies the core row model
automatically. Optional sorting, filtering, and pagination row models are
registered as named slots on `tableFeatures` alongside their feature objects.

The optional `key` option identifies a table to TanStack Table Devtools. Omit
it when devtools are not in use.

## Rendering ownership

TanStack Table does not render markup or styles. The React adapter exposes
table, header, row, and cell objects. Application code owns semantic markup,
keyboard behavior, accessibility attributes, loading and empty states, styles,
dimensions, and responsive behavior.

`table.FlexRender` accepts the header or cell object and renders the matching
column definition, whether that definition is a primitive value or a React
component.

## Stable references

Keep `data`, `columns`, and `features` stable while their contents are unchanged.
Module scope is sufficient for static values. Use React state, query data, or
`useMemo` for values created inside a component.

```tsx
const columns = useMemo(() => makeColumns(), [])
const rows = useMemo(() => response?.rows ?? [], [response?.rows])
```

## State ownership

V9 table state uses TanStack Store atoms. Let the table own a state slice unless
the application must synchronize it with a URL, server request, or another
component. For controlled state, provide the selected value and its matching
change mechanism; otherwise the slice can freeze or drift from application
state.

## Verification

The official quick start assumes an existing React project and supplies no
portable build command. In the host application, verify that:

1. TypeScript accepts the feature-aware `ColumnDef` type.
2. Both headers and rows render through `table.FlexRender`.
3. The development page shows the two rows without a render loop.
4. The host project's test and build scripts pass.

## Sources

- https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/framework/react/guide/table-state.md
- https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/data.md
- https://github.com/TanStack/table/blob/d01c01bedbab0ff6c2641f18b2fc9a11545d9bf6/docs/guide/column-defs.md

## Gaps

The official chain has no complete React project, common entry filename, or
project-level build command. Successful row rendering does not establish the
application's accessibility behavior.
