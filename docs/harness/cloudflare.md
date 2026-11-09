# Cloudflare runtime and deployment

## Project topology

- Find the intended Pages project and public URL from the active repository/account configuration before deploying. Do not assume project names or URLs from another site.
- Static output: `public/`; Pages Advanced Mode Worker: `public/_worker.js`.
- D1 binding: `DB`; KV binding: `GUESTBOOK_LIMITER`.
- Binding names and account resources are project-specific. Never reuse IDs or assume the same resources in another project.

## Routing and local development

- In Advanced Mode, the Worker owns request routing. Route `/api/*` to API handlers and all other requests through `env.ASSETS.fetch(request)` so static assets continue to work.
- Apply D1 schema changes through ordered files in `migrations/`; verify local and remote migration state separately.
- Use local D1 and Wrangler Pages development for ordinary tests. Local state under `.wrangler/` is not production data and must not be committed.
- Check `wrangler.toml` bindings and production environment settings before deploying; reject placeholder IDs for remote deployment.

## Deployment checks

1. Run syntax/build checks and local Pages + D1 API tests.
2. Confirm remote bindings/migrations and the intended Pages project/account.
3. Determine whether Git integration automatically deploys on push; avoid an unnecessary second Wrangler deployment.
4. After deployment, verify the live homepage, API, static assets, security headers, binding-dependent behavior, and actual deployment/commit identity.
5. Report the deployed URL and verified facts. A successful local build or a started deploy command is not evidence that production is updated.