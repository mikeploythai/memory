# Maintenance policy

Memory uses incremental maintenance instead of bulk crawling.

## 1. Read-through maintenance

Every lookup checks the selected page's library version, source, and retrieval date. Refresh a page only when the current task needs newer behavior and the page is stale or contradicted by installed artifacts. Immutable release documentation remains valid unless an erratum is known.

## 2. Weekly integrity audit

A scheduled audit may inspect the catalog and repository metadata for:

- catalog paths that do not resolve;
- malformed or missing frontmatter;
- duplicate pages or catalog rows;
- topic pages missing from the catalog;
- moving-version pages older than seven days;
- repository growth approaching the shard threshold.

The audit reports findings. It does not crawl documentation sites, delete pages, or refresh every entry.

## 3. Bounded cloud curation

Use a cloud agent for a selected batch, such as one framework version or at most twenty catalog repairs. Give it exact paths and authoritative sources. Require a reviewable branch or pull request, a concise change summary, and a fixed stopping condition. Never run an indefinite crawler.

## Storage

Do not auto-delete remote documentation. Keep each Markdown file below 750 KB and store no binaries, archives, dependency trees, or generated search databases. When the repository approaches 4 GB, create a numbered shard instead of continuing to grow the same Git repository.
