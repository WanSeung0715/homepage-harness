# Verification process and lessons learned

## Evidence before completion claims

- Check each effect in its authoritative system: files in the worktree, commits on the remote, deployed HTTP responses, GitHub issue state, or the Search Console property/report.
- A command starting, a browser tab opening, an authorization flow being launched, or a UI click being attempted is not proof of success.
- Re-read the current screen/accessibility information before UI actions. Use a uniquely identified, verified target. If controls cannot be identified reliably, stop rather than repeating speculative clicks.
- Respect the user's explicitly selected tool and boundary (for example, ego/lite). Do not bypass a failed UI operation with CDP, PowerShell, another browser, or API unless the user allows it.
- State completed, blocked, and unverified results separately; never say a sitemap was submitted, issue closed, or deployment completed without observing that state.

## Test discipline

- Test progressively: syntax/static checks, local Worker/Pages and D1, browser E2E, then production smoke checks only when justified.
- Test invalid and boundary inputs as well as normal flows. Verify security headers and the production binding/configuration, not just source code.
- For pagination, use enough deterministic fixtures to cross a page boundary and verify ordering, no duplicates/omissions, loading-state removal, and cleanup.
- For performance, record repeatable conditions and actual artifacts. Explain measurement failures (such as HTTP 429) instead of making unsupported comparisons.
- Run `git diff --check`, inspect the diff, verify synchronized outputs, and confirm the worktree state before final reporting.

## Lessons from prior session mistakes

- **Wrong or stale working directory:** commands were run while the shell was not always at the expected repository root, leading to confusing missing-file checks and repeated path rediscovery. Always resolve and verify the absolute repository path before every batch of reads/edits/tests; stop if it differs.
- **Premature external-action claims:** browser launches and attempted Search Console interactions were confused with property registration or sitemap submission. Only report the action after checking the resulting property/submission status in Search Console.
- **Ignoring the requested automation boundary:** unsupported ego/lite UI interaction led to repeated attempts and exploration of alternate automation. Use only the requested tool; after a reliable control cannot be operated, disclose the blocker and ask for the minimum user action.
- **Unverified or overstated QA outcomes:** production writes, rate limits, issue state, and Lighthouse scores require direct evidence. Minimize production mutations, clean test records and verify absence, retain reports/settings, and do not close unresolved issues.
- **Public guestbook moderation:** do not infer that a suspicious-looking message is disposable. Preserve user content unless deletion/reset scope is explicit; offer review or an authorized reset instead.
- **Tool claims:** reading an `im-not-ai` repository is not the same as running its rewriting skill. Do not claim external tools were used unless invocation and output are verified.