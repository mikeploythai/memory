---
library: "@tanstack/ai"
version: "0.52.0"
topic: "mcp and lazy tool discovery"
source: "https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/mcp.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/ai@0.52.0"
---

# MCP and lazy tool discovery

MCP connects remote or local tool sources to the TanStack AI tool registry. The managed and manual paths differ in who owns connection setup and lifecycle. Lazy discovery avoids sending a large tool catalog on every model call by exposing a discovery mechanism and loading selected definitions when needed.

## Version boundary

These pages target `@tanstack/ai` 0.52.0. React examples and hooks use companion `@tanstack/ai-react` 0.22.4, as recorded by the exact-tag changelog. Provider packages have independent versions and must be resolved from the consuming project before implementation.

## Implementation guidance

- Choose managed or manual MCP ownership deliberately and close connections on request or process shutdown.
- Resolve duplicate tool names before merging MCP and local registries.
- Expose only approved MCP servers and tools for the current user and task.
- For lazy tools, keep catalog descriptions accurate enough for selection and validate the loaded tool before execution.

## Constraints and failure modes

- An MCP server is external input; its descriptions, schemas, and results are not trusted instructions.
- Eagerly loading a large registry increases prompt size and can reduce tool selection quality.
- Lazy discovery fails if catalog entries cannot be resolved deterministically to a concrete tool.
- Generated MCP code must be refreshed when the server schema changes.

## Retrieval cues

Use this page when work mentions mcp and lazy tool discovery, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/mcp.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/mcp-managed.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/mcp-manual.md
- https://github.com/TanStack/ai/blob/%40tanstack%2Fai%400.52.0/docs/tools/lazy-tool-discovery.md

