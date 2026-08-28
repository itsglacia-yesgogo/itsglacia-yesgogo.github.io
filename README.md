# GLACIAS — Hugo site (Ananke + brutalist skin)

Trilingual (EN / 中文 / ES) personal site for Glacia ("Yes"). Hugo with the
Ananke theme (v2.12.0, vendored) re-skinned in the style of WPKoi's "Lalita"
WordPress theme: pink/purple/yellow palette, Kanit + Nunito (Google Fonts),
blob-framed hero image, card grid, timeline, dark quote band.
Custom look lives in `assets/ananke/css/custom.css` + the overrides in
`layouts/` (site-header/hero, page bands, homepage sections, footer).
Hero photo: `static/images/flight.jpg` (airplane wing over clouds; Unsplash,
free license, by Ross Parmly) — swap anytime, keep the filename.
Homepage texts/cards/timeline are edited in the front matter of
`content/_index.<lang>.md`; socials (Instagram/LinkedIn/email) in `hugo.toml`
under `[params]`.

## Edit content
- Homepage: `content/_index.<lang>.md` (front-matter `description` = tagline on the hero)
- About / contact: `content/about.<lang>.md`
- Resources (Google Drive links): `content/resources.<lang>.md`
- Languages: `en`, `zh-tw`, `es` — same filename, different suffix.

## Run locally
Install Hugo (extended), then: `hugo server` → http://localhost:1313

## Deploy to GitHub Pages
1. Create a public repo, push everything.
2. Repo Settings → Pages → Source: **GitHub Actions**.
3. Edit `baseURL` in `hugo.toml` to your Pages URL (the workflow also
   injects the right URL at build time, so this mostly matters for RSS).
4. Push to `main` — the workflow in `.github/workflows/hugo.yml` builds and deploys.

## Notes
- Theme vendored (no submodule) and patched: `css.Sass` → `toCSS` so it
  builds on Hugo 0.123–0.127. CI pins Hugo 0.123.8. To upgrade Hugo past
  0.127, revert that patch (`grep -rn toCSS themes/ananke/layouts`) or
  bump the theme.
- The skin lives in `assets/ananke/css/custom.css` — palette as CSS
  variables at the top (`--purple`, `--pink`, `--yellow`, ...). Avoid
  `min()`/`max()` in CSS (the old Sass pipeline chokes); `clamp()` is fine.
- Events/calendar: planned, not in v1.
