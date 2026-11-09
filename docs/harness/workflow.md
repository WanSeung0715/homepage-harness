# Project workflow and structure

## Before changing code

- Inspect the repository structure, runtime/framework, default branch, remotes, and current working-tree changes before editing.
- Break the request into UI, behavior, API/data, and deployment requirements; preserve the existing conventions and the user's most recent instructions.
- Confirm the working directory and target file paths at each shell step. If the expected root or file is absent, stop and locate the correct project rather than guessing another path.
- Verify supported tooling from project configuration or official documentation before installing dependencies.
- Check whether content exposes personal information before making it public.

## Source and output structure

- This project keeps the editable source `index.html` at the repository root and the Cloudflare Pages output in `public/`.
- When changing the page, synchronize source and output deliberately, then compare their relevant content or hashes.
- Keep user-provided text out of HTML string interpolation; use DOM text APIs such as `textContent`.
- Keep each change scoped to the request. Review `git diff` and `git status` before reporting or creating a commit.

## Reusable pattern for new sites

```text
project/
├── AGENTS.md                 # instruction index
├── docs/harness/             # detailed topic-specific guidance
├── index.html                # editable page source
├── public/
│   ├── index.html            # Pages output
│   ├── og-image.png          # share preview asset, if used
│   └── _worker.js            # Pages Advanced Mode, if needed
├── migrations/               # D1 migrations, if needed
├── wrangler.toml
└── README.md
```

Use only the pieces needed by the new project. Do not copy this site's identifiers, URLs, account/resource IDs, or personal content into another site.

## User-facing completion report

- Summarize what changed, list checks actually run, and identify the exact commit/deployment only after verifying it.
- Separate completed, blocked, and unverified work. Include any remaining user action and its exact destination.
- Do not claim an external editing/rewriting tool was used unless it was actually invoked and its result checked.