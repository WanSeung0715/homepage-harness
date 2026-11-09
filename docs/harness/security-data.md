# Security and guestbook data

## Input and rendering

- Validate all client input again on the server; client-side validation is only a usability aid.
- Enforce documented maximum lengths and reject control/zero-width-only input where appropriate.
- Render guestbook names and messages as text, never as trusted HTML. Exercise XSS payloads and confirm they display inertly.
- Keep password material out of list/API responses. Store only a per-entry salted password hash using the established password-hashing implementation; never log or expose the plaintext.
- Preserve the currently documented password policy and make the UI, Worker validation, and documentation agree.

## Public data and destructive operations

- Guestbook content is public. Do not publish personal data without the user's explicit direction.
- Do not delete an individual public entry or clear the guestbook unless the user clearly authorizes that scope. A suspicious or malformed-looking post should be reported for review rather than silently removed.
- Before destructive data operations, identify the target environment (local/preview/production), explain the scope, and verify that it matches the user's request.
- For tests that write to production, use clearly identifiable test data, remove it using the same authorized mechanism, then query the database/API to verify it is absent. Prefer local/preview tests.

## Abuse controls and privacy

- Current policy: IP-based UTC-hour limits are 20 creates, 10 edit/delete attempts, and 60 likes. Verify code, bindings, UI copy, and documentation together when changing limits.
- KV is eventually consistent; describe its limits as best-effort abuse mitigation, not an exact global atomic quota. Consider Durable Objects only if a strict global counter is required.
- Do not claim IP rate limiting provides unique-person or one-like-per-person enforcement.
- Avoid exposing raw IPs or secrets. Keep local state and credentials out of Git.