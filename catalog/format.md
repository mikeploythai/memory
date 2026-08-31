# Repository format

Documentation pages use this layout:

```text
libraries/<library-slug>/<version-slug>/<topic-slug>.md
```

Each topic begins with YAML frontmatter:

```yaml
---
library: "@scope/package"
version: "1.2.3"
topic: "descriptive topic"
source: "https://official.example/docs/page"
retrieved_at: "YYYY-MM-DD"
source_ref: "optional release tag, commit, or API date"
---
```

Use lowercase ASCII path slugs. Keep one focused topic per page, preserve useful examples, and link to the original authoritative source. Update the topic page before registering it in `libraries.md`.
