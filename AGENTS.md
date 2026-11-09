# Agent guidance index

This file is the repository's entry point and source-of-truth index for agent instructions. Read the relevant linked guidance before changing that area. If instructions conflict, follow the most specific applicable file and preserve the user's latest explicit request.

## Guidance by topic

- [Project workflow and structure](docs/harness/workflow.md): repository discovery, requirements, paths, source/output synchronization, and change management.
- [Security and guestbook data](docs/harness/security-data.md): input handling, passwords, XSS, privacy, destructive actions, and abuse controls.
- [Cloudflare runtime and deployment](docs/harness/cloudflare.md): Pages Advanced Mode, Worker routing, D1/KV, migrations, local development, and production deployment checks.
- [SEO, accessibility, and performance](docs/harness/seo-performance.md): page metadata, social sharing, robots/sitemap/Search Console, accessibility, list loading, and performance measurement.
- [Verification and session lessons](docs/harness/verification-lessons.md): evidence required before reporting completion, UI automation constraints, QA practices, and lessons learned from prior mistakes.

## Working rules

1. Confirm the repository root and current Git state before editing; use absolute paths when referring to project files.
2. Read the applicable topic guidance before implementation and validate every changed or created file afterward.
3. Do not claim an action succeeded until its result is observable in the target system (for example, remote commit, deployed response, Search Console status, or issue state).
4. Report completed, blocked, and unverified work separately. Never imply that opening a page, starting a command, or attempting a UI action completed the task.
5. Do not commit, push, deploy, modify production data, or close issues unless requested or explicitly required by the user's current task.

## Legacy link

[`HOMEPAGE_PLAYBOOK.md`](HOMEPAGE_PLAYBOOK.md) is retained as a pointer for existing README links. The topic files under `docs/harness/` are the detailed guidance source.