---
library: "@tanstack/charts"
version: "0.16.0"
topic: "stability, installation, and react quick start"
source: "https://github.com/TanStack/charts/blob/v0.16.0/docs/stability.md"
retrieved_at: "2026-08-31"
source_ref: "v0.16.0"
---

# Stability, installation, and React quick start

Charts 0.16.0 is an alpha release. Its package uses explicit ESM subpaths for the core grammar, scales, adapters, renderers, and optional capabilities. A React chart is built from a stable definition and rendered through the React adapter; the chart follows its container unless a size is explicitly owned elsewhere.

## Implementation guidance

- Pin the 0.16.x package when reproducibility matters; alpha minor releases may change APIs.
- Import framework and scale features from documented subpaths so tree shaking can preserve optional boundaries.
- Keep a chart definition stable until captured data or options change.
- Provide an accessible label and a container with measurable dimensions.

## Constraints and failure modes

- Do not use hosted `latest` as a version-pinned source; it follows unreleased main.
- Recreating a definition on every render makes identity the update boundary and can reset work or state.
- A zero-size or unmeasurable container cannot produce a useful responsive layout.
- Assume no semver-stable API across alpha minor releases.

## Retrieval cues

Use this page when work mentions stability, installation, and react quick start, or when an implementation touches the APIs and lifecycle boundaries described above. Re-open the exact-tag sources before relying on signatures not reproduced here; this page organizes the documented behavior but does not replace the complete generated API reference.

## Sources

- https://github.com/TanStack/charts/blob/v0.16.0/docs/stability.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/installation.md
- https://github.com/TanStack/charts/blob/v0.16.0/docs/framework/react/quick-start.md

