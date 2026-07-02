# Another Realm Compliance — Coming-Soon Page

Single-page static coming-soon site for **Another Realm Compliance**, a DBA of
CBUS Express Transport Limited LLC (Columbus, Ohio). Offers third-party UST / AST
compliance testing. Hosted on Netlify (publish root `.`, auto-deploys on push to `main`).

## DO NOT TOUCH
- `netlify.toml` — security headers (X-Frame-Options: DENY, X-Content-Type-Options: nosniff). No edits.
- Supabase lead-capture wiring in `index.html`: the `capture-lead` endpoint URL, the POST
  field names, and payload values (`entity=CBUS`, `dba=Another Realm Compliance`, `source=web:home`).
- The honeypot field `_hp` — keep it, keep it hidden.

## Brand
- Safety Orange `#FF6B00` (CTAs, accents, rules) · Federal Navy `#1E3A5F` (headings, footer band)
- Steel Gray `#8A94A0` (captions, hatch) · White background/fields
- Fonts: Rajdhani 500/600/700 (headings/wordmark, uppercase) · Inter (body)

## Discipline
Single-file static page (`index.html`, inline CSS). No build step, no framework, no npm.
One-deploy discipline: make all changes, then push once.
