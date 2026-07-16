# Another Realm Compliance — Website

Multi-page static marketing site for **Another Realm Compliance**, a DBA of
CBUS Express Transport Limited (Columbus, Ohio). Offers third-party UST / AST
compliance testing. Hosted on Netlify (publish root `.`, auto-deploys on push to `main`).

## Structure (multi-page static, no build step)
- `index.html` (Home) · `services.html` · `certifications.html` · `portal.html` ·
  `about.html` · `contact.html`
- `style.<hash>.css` — one shared stylesheet linked by every page (content-hash fingerprinted; see "Cached assets" below).
- Shared header/nav + navy footer band are copied byte-identical into each page
  (no server includes). `resources.html` nav slot is reserved as an HTML comment.
- `favicon.<hash>.svg`, `og-image.<hash>.png` (both content-hash fingerprinted), `robots.txt` (allow-all), `sitemap.xml`.

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

## Cached assets — content-hash fingerprinting (REQUIRED)
`style.css`, `favicon.svg`, and `og-image.png` are served with a long immutable
cache (`public, max-age=31536000, immutable` via netlify.toml's `/*.css` /
`/*.svg` / `/*.png` rules). To make that safe, each filename embeds a short
content hash: `style.<hash>.css`, `favicon.<hash>.svg`, `og-image.<hash>.png`.

**Rule:** ANY edit to one of these three files MUST also (1) recompute its hash,
(2) rename the file to the new hash, and (3) update every reference in all HTML
pages (stylesheet `<link>`, favicon `<link>`, and the absolute `og:image` meta on
every page). Never edit these files in place under the same filename — the old
immutable cache would serve stale bytes.

Repeatable manual steps (no build step exists):
1. `h=$(sha256sum <file> | cut -c1-8)`
2. `git mv <name>.<ext> <name>.$h.<ext>`
3. Replace the old filename with the new one across all `*.html` (grep to confirm
   zero stale references remain).
HTML pages themselves are NOT fingerprinted — they stay on `no-cache,
must-revalidate` with clean URLs.

## Discipline
Static HTML + one shared CSS. No framework, no build step, no npm.
One-deploy discipline: make all changes, then push once.
