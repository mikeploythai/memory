---
library: "@tanstack/react-start"
version: "1.168.30"
topic: "getting started and project creation"
source: "https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/getting-started.md"
retrieved_at: "2026-08-31"
source_ref: "@tanstack/react-start@1.168.30 / 62a191baa068e9a2d27815cc82fb2a16690fedea"
---

# Getting started and project creation

The exact-tag documentation offers four starting paths. Choose one deliberately rather than mixing files from different templates.

1. TanStack Builder is the hosted setup flow.
2. The local CLI scaffolds a project and prompts for a package manager and optional add-ons:

   ```sh
   npx @tanstack/cli@latest create
   ```

3. An official example can be cloned with `gitpick`, then installed and started:

   ```sh
   npx gitpick TanStack/router/tree/main/examples/react/start-basic start-basic
   cd start-basic
   npm install
   npm run dev
   ```

4. Manual setup is documented in `build-from-scratch.md`.

The first three routes are convenience paths and may follow moving Builder, CLI, or `main` example content. That is useful for a new application targeting the current ecosystem, but it does not by itself reproduce Start 1.168.30. For an exact-version build, use the pinned manual setup as the authority, install the requested Start and Router versions explicitly, and compare scaffolded configuration with the exact-tag docs before accepting it.

After creation, verify that the project has a `src/router.tsx`, a root route at `src/routes/__root.tsx`, and build-tool configuration containing the Start plugin. Run the development command and confirm that `routeTree.gen.ts` is generated. Do not hand-maintain that generated file.

The next conceptual step is `routing.md`. For full-stack behavior, continue with `server-functions.md`, `environment-variables-and-secrets.md`, and `middleware.md`. When migrating an existing application, do not treat the greenfield scaffold as a migration plan; use the source-framework migration guide and preserve source/target version boundaries.

## Sources

- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/getting-started.md
- https://github.com/TanStack/router/blob/62a191baa068e9a2d27815cc82fb2a16690fedea/docs/start/framework/react/build-from-scratch.md


