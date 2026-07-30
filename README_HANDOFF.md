# ALI Website Renewal — Handoff

## Build
- Version: final image build v1
- Built: 2026-07-30
- Source image page: Notion「ALIのHP画像」 (`https://app.notion.com/p/3ad8441cb1a180a79f37fb86508cb1e7`)
- Entry point: `index.html`

## Pages
- `/` → `index.html`
- `/tech` → `tech/index.html`
- `/company` → `company/index.html`
- `/recruit` → `recruit/index.html`
- `/news` → `news/index.html`
- `/contact` → `contact/index.html`

## Image policy
- TOP hero: three PC masters plus dedicated center crops for SP.
- TOP CONTACT: employee group photo; separate PC/SP variants.
- Recruit MESSAGE: employee group photo with original lineup preserved.
- Product case images: six 3:2 assets; first three reused on TOP.
- Lower page headers reuse the closest master asset to keep tone consistent.

See `asset-manifest.json` for exact assignments.

## Remaining production checks
- Replace the Google Map placeholder with the production map/embed.
- Confirm ISO registration details and equipment counts before launch.
- Confirm recruiting conditions, telephone reception hours, and form fields.
- Confirm that all generated machining examples are approved for public use.
- Convert absolute links only if deploying below a subdirectory rather than domain root.

## Preview
Run a static server at this folder root, for example:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080/`.
