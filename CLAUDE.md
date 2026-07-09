# Another Realm Compliance — Website

Multi-page static marketing site for **Another Realm Compliance**, a DBA of
CBUS Express Transport Limited (Columbus, Ohio). Offers third-party UST / AST
compliance testing. Hosted on Netlify (publish root `.`, auto-deploys on push to `main`).

## Structure (multi-page static, no build step)
- `index.html` (Home) · `services.html` · `certifications.html` · `portal.html` ·
  `about.html` · `contact.html`
- `style.css` — one shared stylesheet linked by every page.
- Shared header/nav + navy footer band are copied byte-identical into each page
  (no server includes). `resources.html` nav slot is reserved as an HTML comment.
- `favicon.svg`, `robots.txt` (allow-all), `sitemap.xml`, `og-image.png`.

## DO NOT TOUCH
- `netlify.toml` — security headers (X-Frame-Options: DENY, X-Content-Type-Options: nosniff). No edits.
- Supabase lead-capture wiring (now in `contact.html`): the `capture-lead` endpoint URL,
  the POST field names, and payload values (`entity=CBUS`, `dba=Another Realm Compliance`,
  `source=web:home`). Wiring is byte-identical to the original — do not alter the fetch,
  field names, or values.
- The honeypot field `_hp` — keep it, keep it hidden.
- Footer legal line must read EXACTLY: "Another Realm Compliance is a DBA of CBUS
  Express Transport Limited." — no "LLC" appended.
- No certification claims outside `certifications.html`; never say "certified" in About prose.
- Never publish certification numbers, issuing-body names, or expiry dates anywhere.
- No reference to anotherrealmai.com or cbus-express.com on any page.

## Brand
- Safety Orange `#FF6B00` (CTAs, accents, checks, rules) · Federal Navy `#1E3A5F`
  (headings, header, footer band, linework) · Steel Gray `#8A94A0` (captions, hatch) · White background.
- Fonts: Rajdhani 500/600/700 (headings/wordmark/nav, uppercase) · Inter 400/500/600 (body).
- Section divider motif: thin dashed navy "grade line" with sparse gray hatch ticks (`.grade-divider`).

## Discipline
Static HTML + one shared CSS. No framework, no build step, no npm.
One-deploy discipline: make all changes, then push once.
