---
library: "@tanstack/ai"
version: "0.52.0"
topic: "streaming chat with React"
source: "https://tanstack.com/ai/latest/docs/getting-started/quick-start"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0; @tanstack/ai-react@0.22.4; release candidate"
---

# Streaming chat with TanStack AI and React

TanStack AI separates the framework-neutral chat runtime, React hooks, and model-provider adapters. The packages do not share one version number. The official project described the architecture as release candidate in August 2026, but it remains pre-v1 software.

## Installation

```sh
npm install @tanstack/ai @tanstack/ai-react @tanstack/ai-openai
```

## Server and client shape

Keep provider credentials on the server. A server handler creates a stream and returns it as server-sent events.

```ts
import { chat, chatParamsFromRequest, toServerSentEventsResponse } from '@tanstack/ai'
import { openaiText } from '@tanstack/ai-openai'

export async function POST(request: Request) {
  const params = await chatParamsFromRequest(request)
  const stream = chat({
    adapter: openaiText('gpt-5.6'),
    messages: params.messages,
    threadId: params.threadId,
    runId: params.runId,
  })
  return toServerSentEventsResponse(stream)
}
```

Connect the React hook to that endpoint:

```tsx
import { useChat, fetchServerSentEvents } from '@tanstack/ai-react'

const chat = useChat({
  connection: fetchServerSentEvents('/api/chat'),
})

chat.sendMessage('Hello')
```

## Notes

- Provider credentials belong on the server unless an application intentionally implements the documented bring-your-own-key flow.
- Pin every TanStack AI package independently.
- Pre-v1 APIs may change even when the overall architecture is considered release candidate.

## Sources

- https://tanstack.com/ai/latest/docs/api/ai-react
- https://tanstack.com/blog/tanstack-ai-rc
- https://github.com/TanStack/ai/blob/main/packages/ai/CHANGELOG.md
