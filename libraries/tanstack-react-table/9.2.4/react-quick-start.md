---
library: "@tanstack/react-table"
version: "9.2.4"
topic: "React quick start"
source: "https://tanstack.com/table/latest/docs/framework/react/quick-start"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-table@9.2.4; release commit d01c01b; moving v9 docs"
---

# React tables with TanStack Table v9

TanStack Table is headless: it supplies table state and row-processing logic, while the application owns markup and styling. This page uses v9 APIs and must not be mixed with v8 examples.

## Installation

```sh
npm install @tanstack/react-table
```

Version 9.2.4 requires React 18 or newer and declares Node 20 or newer.

## Create and render a table

```tsx
import { tableFeatures, useTable, type ColumnDef } from '@tanstack/react-table'

type Person = { name: string; age: number }
const features = tableFeatures({})
const data: Person[] = [{ name: 'Ada', age: 36 }]

const columns: Array<ColumnDef<typeof features, Person>> = [
  { accessorKey: 'name', header: 'Name' },
  { accessorKey: 'age', header: 'Age' },
]

export function People() {
  const table = useTable({ features, data, columns })

  return (
    <table>
      <thead>
        {table.getHeaderGroups().map((group) => (
          <tr key={group.id}>
            {group.headers.map((header) => (
              <th key={header.id}>
                {header.isPlaceholder ? null : <table.FlexRender header={header} />}
              </th>
            ))}
          </tr>
        ))}
      </thead>
      <tbody>
        {table.getRowModel().rows.map((row) => (
          <tr key={row.id}>
            {row.getAllCells().map((cell) => (
              <td key={cell.id}><table.FlexRender cell={cell} /></td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  )
}
```

## Notes

- Keep `data` and `columns` references stable between renders.
- The core row model is included; optional sorting, filtering, and pagination features must be registered.
- v8 uses `useReactTable`, `getCoreRowModel`, and standalone `flexRender`. Use the migration guide rather than combining generations.

## Sources

- https://tanstack.com/table/latest/docs/installation
- https://tanstack.com/table/latest/docs/framework/react/guide/migrating
- https://github.com/TanStack/table/releases
