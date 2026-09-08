---
library: "@tanstack/pacer"
version: "0.22.0"
topic: "coverage map"
source: "https://tanstack.com/pacer/latest/llms.txt"
retrieved_at: "2026-08-31"
source_ref: "c75895520669b08dc8946b42e1a6d529ca977230"
---

# TanStack Pacer 0.22.0 coverage map

This bounded set covers core Pacer `0.22.0`, records independently versioned
adapters and devtools, and treats Pacer Lite `0.2.2` as a separate release ref.
TanStack labels the product beta.

## Sources

| Source | Ref or behavior | Result |
|---|---|---|
| [Root TanStack llms index](https://tanstack.com/llms.txt) | moving site index | Identifies Pacer, packages, repository, and product index |
| [Pacer llms index](https://tanstack.com/pacer/latest/llms.txt) | `main` | Full route inventory for guides, API, adapters, and examples |
| [Markdown docs index](https://tanstack.com/pacer/latest/docs/index.md) | `main` | Same routing corpus as product `llms.txt` |
| `https://tanstack.com/pacer/latest/llms-full.txt` | checked 2026-08-31 | Not present; HTTP 404 |
| [Core release repository](https://github.com/TanStack/pacer/tree/c75895520669b08dc8946b42e1a6d529ca977230) | immutable commit | Core, adapters, current devtools |
| [Pacer Lite release repository](https://github.com/TanStack/pacer/tree/a894009100aeb373965d4121eb92a1af634af012/packages/pacer-lite) | immutable commit | Lite `0.2.2` |
| [Releases](https://github.com/TanStack/pacer/releases) | package tags | Confirms independent package versions and changelogs |

Hosted `latest` documentation followed repository `main` at
`e063ad753740080232b746b265ad4db5a845f7b3` when checked. Version-sensitive
signatures must be reconciled against the release commit.

## Bootstrap chain

| Requirement | Status | Evidence or gap |
|---|---|---|
| Package choice and prerequisites | partial | [Package choice](package-choice-installation-and-quick-start.md) covers core, adapters, and Lite; runtime/tooling ranges are absent |
| Project creation | not present | No application creator or starter command in Pacer docs |
| Installation commands | partial | npm commands are indexed for core and all four adapters, but the commands are unpinned |
| Getting started / quick start | partial | Core class/function examples exist; adapter quick starts are routed by package but are not retained as complete host applications |
| Manual setup | not present | No build-from-scratch application page |
| Required files/configuration | partial | Core utility snippets and adapter/provider API routing exist; filenames, adapter setup, and entry wiring are not supplied |
| Core mental model | partial | Utility selection and debounce/throttle concepts are indexed; exact rate-limit, queue, and batch option contracts are deferred |
| Minimal runnable example | partial | Core snippets still require concrete functions and a host application; the React inventory is not a complete runnable project |
| Run/build/verification | blocked | No scripts, run command, test command, build command, or observable automated check |
| Likely setup mistakes | partial | Package choice, selector behavior, keys for devtools, and policy mismatch are covered; no troubleshooting section |

## Task readiness

| Task | Status | Indexed evidence |
|---|---|---|
| Greenfield setup | blocked | Missing project creation, prerequisites, required files, and verification/build commands |
| Add common feature | partial | Core [debounce/throttle/rate-limit](debounce-throttle-and-rate-limit.md) concepts are indexed, but exact rate-limit options are deferred; React [queues/batches/async](../../tanstack-react-pacer/0.23.0/queues-batches-async-retry-and-persistence.md) defers exact batch triggers, retry contracts, persistence schemas, and migration behavior |
| Debug timing/state behavior | partial | API/state selectors and devtools are covered; no dedicated troubleshooting workflow |
| Migration | blocked | No migration guides; breaking changes remain in package changelogs |
| Production/build concerns | partial | Devtools production behavior is covered; no complete application build or server-runtime guidance |

## Source section mapping

| Substantive source section | Indexed page or status |
|---|---|
| Overview, installation, quick start | [package choice, installation, and quick start](package-choice-installation-and-quick-start.md) |
| Utility-selection guide | [package choice](package-choice-installation-and-quick-start.md) and [debounce/throttle/rate limit](debounce-throttle-and-rate-limit.md) |
| React, Preact, Solid, Angular adapters | [core, adapter, and devtools API map](core-adapter-and-devtools-api-map.md) |
| Devtools | [core, adapter, and devtools API map](core-adapter-and-devtools-api-map.md) |
| Sync debounce/throttle/rate-limit guides for five environments | partially indexed in [debounce/throttle/rate limit](debounce-throttle-and-rate-limit.md); exact rate-limit options and repeated framework syntax are deferred |
| Sync queue/batch guides for five environments | React concepts are in [queues, batches, async retry, and persistence](../../tanstack-react-pacer/0.23.0/queues-batches-async-retry-and-persistence.md); exact batch option names and other framework implementations are deferred |
| Five async utility guides for five environments | React queue and batch concepts are indexed; exact contracts and repeated framework pages are deferred |
| Async retrying guides for five environments | React retry considerations are [partially indexed](../../tanstack-react-pacer/0.23.0/queues-batches-async-retry-and-persistence.md); release-specific retry and abort options are deferred |
| Core generated API | [core, adapter, and devtools API map](core-adapter-and-devtools-api-map.md); symbols retrieved on demand |
| Four adapter API indexes | [core, adapter, and devtools API map](core-adapter-and-devtools-api-map.md) |
| Utility example galleries | representative examples indexed; full galleries deferred |
| React Query prefetch examples | deferred; not required for core readiness claims |
| Pacer Lite examples | package choice indexed; complete Lite API details deferred |

## Recipes, warnings, and operational coverage

| Category | Coverage |
|---|---|
| Common recipes | Search debounce and event throttle are represented; quota, upload queue, grouped batch, retry, and persistence recipes remain partial until exact contracts are retained |
| Reusable patterns | Core option helpers and keyed devtools registration are mapped; React state selectors and `Subscribe` are partial adapter coverage |
| Warnings / anti-patterns | Do not debounce work that must run; do not treat client rate limits as security; do not infer shared versions |
| Troubleshooting | not present as a dedicated section; partial coverage through state and devtools |
| Migrations | not present; package changelogs contain breaking changes but are not a migration chain |
| API reference | core and four adapters mapped; generated symbol pages deferred |
| Persistence | React queue/rate-limit persistence APIs are named, but exact persister contracts, durable-storage behavior, and cross-version schema migration are unverified |
| Production | default devtools no-op and explicit production import covered; broader build guidance absent |

## Version and package mismatches

| Package | Version | Pin |
|---|---:|---|
| `@tanstack/pacer` | `0.22.0` | `c758955` |
| `@tanstack/pacer-lite` | `0.2.2` | `a894009` |
| React and Preact adapters | `0.23.0` | `c758955` |
| Solid adapter | `0.22.0` | `c758955` |
| Angular adapter | `0.24.0` | `c758955` |
| Core devtools | `1.4.0` | `c758955` |
| React devtools adapter | `0.8.0` | `c758955` |
| Preact and Solid devtools adapters | `0.7.0` | `c758955` |

The top-level installation page omits Preact despite its published adapter and
official adapter page. Devtools docs omit Preact setup and mark Angular as
“Coming soon.” These are documentation gaps, not evidence that the packages
share another package's behavior.

## Meaningful gaps

- No complete greenfield bootstrap or verification/build command.
- No migration or troubleshooting guide.
- Preact is omitted from top-level installation and devtools setup.
- Angular devtools are not available in the documented setup.
- Pacer Lite lacks documentation depth comparable to core.
- No product-level `llms-full.txt`; hosted pages track moving `main`.

## Bounded stopping point

This batch covers core package choice, first-use snippets, timing-policy
selection, framework/API routing, and devtools, plus a separately versioned
React inventory for queues, batches, retry, and persistence. It defers exact
rate-limit, queue, batch, retry, abort, and persister contracts, repeated
framework guides, example galleries, generated symbol pages, and changelog
synthesis. Feature work remains partial; greenfield and migration readiness
remain blocked.

