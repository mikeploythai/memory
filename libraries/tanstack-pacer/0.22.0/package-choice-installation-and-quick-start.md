---
library: "@tanstack/pacer"
version: "0.22.0"
topic: "package choice installation and quick start"
source: "https://github.com/TanStack/pacer/blob/c75895520669b08dc8946b42e1a6d529ca977230/docs/installation.md"
retrieved_at: "2026-08-31"
source_ref: "c75895520669b08dc8946b42e1a6d529ca977230"
---

# Package choice, installation, and quick start

TanStack Pacer controls when functions run through debouncing, throttling,
rate limiting, queues, and batches. The product documentation labels it beta.

## Choose core, an adapter, or Lite

| Use case | Package | Version at retrieval |
|---|---|---:|
| Vanilla application with reactive state/devtools support | `@tanstack/pacer` | `0.22.0` |
| React application | `@tanstack/react-pacer` | `0.23.0` |
| Preact application | `@tanstack/preact-pacer` | `0.23.0` |
| Solid application | `@tanstack/solid-pacer` | `0.22.0` |
| Angular application | `@tanstack/angular-pacer` | `0.24.0` |
| Small library without reactivity/devtools | `@tanstack/pacer-lite` | `0.2.2` |

Framework adapters re-export core, add lifecycle cleanup, and expose reactive
framework APIs. Do not install core separately unless the application has an
independent reason to depend on it.

Pacer Lite omits TanStack Store integration, framework adapters, devtools, and
some advanced options. Its release is separately pinned to commit
`a894009100aeb373965d4121eb92a1af634af012`, not the core `0.22.0` commit.

## Install

Vanilla core:

```sh
npm install @tanstack/pacer
```

React:

```sh
npm install @tanstack/react-pacer
```

Preact, Solid, and Angular adapter pages provide these commands:

```sh
npm install @tanstack/preact-pacer
npm install @tanstack/solid-pacer
npm install @tanstack/angular-pacer
```

The top-level installation page lists React, Solid, and Angular but omits
Preact. The official Preact adapter page confirms the Preact package and exact
command.

## Choose a timing policy

| Utility | Behavior under frequent calls | Typical fit |
|---|---|---|
| Debouncer | Discards earlier calls and runs the latest after activity stops | search, validation, autosave |
| Throttler | Limits execution to a steady interval | scroll, resize, progress updates |
| Rate limiter | Executes until a quota is exhausted, then rejects | client quotas and burst limits |
| Queuer | Buffers every item and processes them in order | uploads and work that must not be dropped |
| Batcher | Groups several items into one execution | bulk requests and grouped writes |

Use an async variant when the controlled function returns a promise and needs
async result, error, retry, or abort handling.

## Minimal core class usage

```ts
import { Debouncer } from '@tanstack/pacer'

const debouncer = new Debouncer(fn, { wait: 500 })

debouncer.maybeExecute(args)
debouncer.cancel()
debouncer.flush()
```

The quick start uses placeholder `fn`, `options`, and `args`; provide concrete
application values in a real entry file.

## Minimal function usage

```ts
import { debounce } from '@tanstack/pacer'

const debouncedFn = debounce(fn, { wait: 500 })
debouncedFn(args)
```

## Shared option helper

```ts
import { Debouncer, debouncerOptions } from '@tanstack/pacer'

const commonOptions = debouncerOptions({
  wait: 1000,
  leading: false,
  trailing: true,
})

const debouncer = new Debouncer(fn, {
  ...commonOptions,
  key: 'searchDebouncer',
})
```

Adapter-specific hooks and provider APIs belong under each adapter's package
and version. The React queue, batch, retry, and persistence inventory is stored
under [`@tanstack/react-pacer@0.23.0`](../../tanstack-react-pacer/0.23.0/queues-batches-async-retry-and-persistence.md).

## Verification and setup gaps

The official pages omit project creation, supported runtime/tooling ranges,
filenames, package scripts, and a run/build/test command. The examples describe
observable timing behavior but are not a standalone application. Bootstrap is
therefore partial and cannot support a greenfield-ready claim.

## Sources

- [Overview](https://tanstack.com/pacer/latest/docs/overview.md)
- [Installation](https://tanstack.com/pacer/latest/docs/installation.md)
- [Quick start](https://tanstack.com/pacer/latest/docs/quick-start.md)
- [Utility selection](https://tanstack.com/pacer/latest/docs/guides/which-pacer-utility-should-i-choose.md)
- [Preact adapter](https://tanstack.com/pacer/latest/docs/framework/preact/adapter.md)
- [Core release](https://github.com/TanStack/pacer/releases/tag/%40tanstack%2Fpacer%400.22.0)
- [Pacer Lite release source](https://github.com/TanStack/pacer/tree/a894009100aeb373965d4121eb92a1af634af012/packages/pacer-lite)
