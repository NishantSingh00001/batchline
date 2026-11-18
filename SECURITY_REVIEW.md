# Security Review — Batchline

Batchline is a fully static, client-side traceability workbench (`index.html`
+ `app.js`, 8 hash-routed views). All data (ingredient lots, production runs,
dispatch notes, quality checks, supplier records, activity log) is stored only
in browser `localStorage`. Confirmed no `fetch`/`XMLHttpRequest`/`WebSocket`
call anywhere in `app.js`/`index.html` — nothing leaves the browser except the
optional CDN loads of Three.js and GSAP for the decorative vessel scene (with
a non-interactive inline SVG fallback if those fail to load).

## 20-point pen-test checklist

| # | Check | Applicable? | Notes |
|---|-------|-------------|-------|
| 1 | HTTP/2 Rapid Reset (CVE-2023-44487) | N/A | No server component in this repo. |
| 2 | bcrypt 72-byte truncation | N/A | No password hashing. |
| 3 | SAML signature bypass (CVE-2024-45409) | N/A | No SAML/SSO. |
| 4 | nOAuth | N/A | No OAuth/auth of any kind. |
| 5 | GraphQL alias batching | N/A | No GraphQL. |
| 6 | TOTP replay (RFC 6238 §5.2) | N/A | No TOTP/2FA. |
| 7 | ReDoS | No | No user-supplied-pattern regexes; search/filter logic uses plain `.includes()`/`.toLowerCase()`, not regex. |
| 8 | JWT algorithm confusion | N/A | No JWTs. |
| 9 | HTTP request smuggling | N/A | No server. |
| 10 | Web cache poisoning | N/A | No server/cache layer. |
| 11 | Spoofed X-Forwarded-For | N/A | No server-side request handling. |
| 12 | Postgres views bypassing RLS | N/A | No database. |
| 13 | `Math.random()` for security tokens | No | `Math.random()` is used once (`mockRecall()`, `app.js:43`) to pick a random demo lot for a tabletop drill — not a security token. Record IDs use `Date.now()`-based strings, also not security-sensitive. |
| 14 | Timing attacks on secret comparison | N/A | No secrets/credentials to compare. |
| 15 | Padding oracle | N/A | No encryption/decryption. |
| 16 | Server-side prototype pollution | N/A | No server; `localStorage` state is loaded into a fixed object shape, not deep-merged from attacker input. |
| 17 | Server-side template injection | N/A | No server, no templating engine. |
| 18 | XXE | N/A | No XML parsing (JSON export/import, CSV export only). |
| 19 | Cross-site WebSocket hijacking | N/A | No WebSockets. |
| 20 | Unicode username normalization | N/A | No usernames/accounts. |

## Findings outside the 20-point list

None. Every page-rendering function (`home`, `stock`, `newLot`, `batches`,
`production`, `trace`/`traceResult`, `dispatches`, `quality`, `suppliers`,
plus the global search results) consistently passes user-entered text —
ingredient names, supplier names/contacts, batch products/notes, dispatch
destinations/references, quality-check values/notes — through `esc()`
(`app.js:15`, escaping `&`/`<`/`>`/`"`/`'`) before interpolating it into
`innerHTML`. The two non-escaped template spots (`vesselFallback`'s SVG and
the static hero/help copy) are fixed markup with no user input. JSON
import/restore of a backup replaces the full state object rather than
deep-merging into existing structures.

No fixes are proposed or applied in this review.
