---
library: "@tanstack/ai"
version: "0.52.0"
topic: "bootstrap for React and server applications"
source: "https://github.com/TanStack/ai/blob/b899fe5328f2907e5abbaa9c11b8f486caec229f/docs/getting-started/quick-start.md"
retrieved_at: "2026-08-31"
source_ref: "b899fe5328f2907e5abbaa9c11b8f486caec229f"
---

# Bootstrap TanStack AI for React and server applications

TanStack AI separates the server activity API, provider adapters, the headless
client, and framework bindings. These packages have independent versions.
Do not copy the `@tanstack/ai` version onto companion packages.

## Version set checked for this release

| Role | Package | Checked stable version |
|---|---|---:|
| Core server activities | `@tanstack/ai` | `0.52.0` |
| Headless browser client | `@tanstack/ai-client` | `0.29.2` |
| React binding | `@tanstack/ai-react` | `0.22.4` |
| OpenAI adapter | `@tanstack/ai-openai` | `0.22.3` |
| Anthropic adapter | `@tanstack/ai-anthropic` | `0.18.3` |
| Gemini adapter | `@tanstack/ai-gemini` | `0.26.4` |
| OpenRouter adapter | `@tanstack/ai-openrouter` | `0.19.5` |

The repository manifests and npm `latest` metadata agreed on these versions on
the retrieval date. The core release tag alone does not prove companion-package
versions.

## Package selection

Install the core package for server-side AI activities:

```sh
npm i @tanstack/ai
```

Add one provider adapter. For the OpenAI adapter used by the official API
example:

```sh
npm i @tanstack/ai-openai
```

A React chat client also needs the headless client and React binding:

```sh
npm i @tanstack/ai-client @tanstack/ai-react
```

Pin the versions from the table when reproducibility matters. The commands
above intentionally show package selection rather than claiming an unverified
lockfile or package-manager policy.

## Verified core call shape

The official `@tanstack/ai` API page documents this `chat()` shape:

```ts
import { chat, maxIterations } from '@tanstack/ai'
import { openaiText } from '@tanstack/ai-openai'
import { myTool } from './tools'

const stream = chat({
  adapter: openaiText('gpt-5.2'),
  messages: [{ role: 'user', content: 'Hello!' }],
  tools: [myTool],
  systemPrompts: ['You are a helpful assistant'],
  agentLoopStrategy: maxIterations(20),
})
```

`chat()` returns a streaming response. Provider-specific model names and
credentials belong to the selected adapter, not to the core package.

## Required application boundary

A complete web application needs two cooperating halves:

1. A trusted server module creates the provider adapter and calls `chat()`.
2. The server converts the stream to the transport used by the client.
3. The browser uses `@tanstack/ai-client` directly or a framework binding.
4. Secrets remain on the trusted server unless the application deliberately
   implements the documented BYOK flow.

The React and server-only quick starts are separate authoritative variants.
Keep each variant's filenames, transport helper, request parsing, and component
code together. Do not splice a server-only example into a framework example
without checking their request formats.

## Bootstrap candidates

The `0.52.0` release also contains dedicated quick starts for React Native,
Vue, Svelte, Angular, and Octane. The moving hosted index no longer lists four
of those framework pages, so use the immutable release files when indexing
this version.

## Verification and known gaps

The bounded evidence collected for this draft verifies package identities,
versions, installation commands, and the core `chat()` call shape. It does not
verify a complete project filename set, environment-variable name, development
script, build command, or observable browser result for one framework variant.

Therefore this page is **partial** for greenfield bootstrap. Before marking it
ready, copy one official quick start's complete files and exact run/build check
from the pinned release without paraphrasing implementation-sensitive details.

## Sources

- https://tanstack.com/ai/latest/docs/getting-started/overview.md
- https://tanstack.com/ai/latest/docs/getting-started/quick-start.md
- https://tanstack.com/ai/latest/docs/getting-started/quick-start-server.md
- https://tanstack.com/ai/latest/docs/getting-started/quick-start-react-native.md
- https://tanstack.com/ai/latest/docs/api/ai.md
- https://github.com/TanStack/ai/tree/b899fe5328f2907e5abbaa9c11b8f486caec229f/docs/getting-started
