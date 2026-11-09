# SEO, accessibility, and performance

## Page and sharing metadata

- Set an accurate, page-specific `<title>` and meta description. Do not invent facts or repeat keywords unnaturally.
- Set canonical URL, Open Graph title/description/image/url, and Twitter card metadata using the verified public URL and a share image served in the deployment output.
- Prefer broadly supported PNG/JPEG share images at 1200×630; if SVG is used, note that some social platforms may not render it.
- Only request font families and weights actually used. Consider `display=swap` and necessary preconnects, then test visual stability and accessibility.

## Crawling and Search Console

- Put `robots.txt` and a valid XML sitemap in the deployed root. Sitemap entries must use absolute canonical page URLs and omit API routes.
- Verify deployed HTTP responses and parse the deployed XML; local files alone do not establish production correctness.
- Search Console property ownership, sitemap submission, and processing status must be checked in Search Console itself. File deployment, opening a dashboard, or attempting an action is not submission evidence.
- Complete Search Console actions only with the user's requested browser/tool. If the tool cannot reliably operate the required control, stop and state the blocker without switching to an unapproved automation route.

## Accessible loading and long lists

- Choose pagination for chronological/archive-style lists where preserving reading position and reaching the page footer matter; use infinite scrolling only for feed-style discovery where it improves the experience.
- Bound API page size and use a stable cursor/order. Test duplicates, omissions, empty state, end-of-list, and invalid cursor behavior.
- Use a concise skeleton for initial and incremental loading. Announce loading/results/errors with suitable live status semantics; support reduced motion and visible keyboard focus.
- Test narrow mobile and wide desktop layouts; constrain long-form input widths so the form remains readable on large screens.

## Performance measurement

- Measure the live/deployed page on both mobile and desktop when requested, and record tool/version, URL, settings, score, and report artifact.
- Lighthouse lab scores vary: compare consistent runs and avoid presenting one run as a stable field result.
- If PageSpeed or another external service returns quota/network errors, report the error and do not fabricate results.
- Identify the measured bottleneck before optimizing. Re-measure after changes and check layout/behavior regressions.