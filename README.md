# Followthrough — landing site

Marketing landing page for [followthroughqa.com](https://followthroughqa.com).

Static HTML/CSS. No build step. Deploys to Cloudflare Pages on every push to `main`.

## Stack

- Hand-written HTML + CSS
- Self-hosted fonts (Space Grotesk, Inter, JetBrains Mono) as `.woff2` — no Google Fonts dependency at runtime
- SVG wordmark and marks inlined for `currentColor` flexibility
- Inherits color, type, and spacing tokens from the Followthrough brand system

## Local preview

```powershell
python -m http.server 5173 --directory .
# open http://127.0.0.1:5173
```

## Layout

```
.
├── index.html
├── styles.css
├── README.md
├── .gitignore
└── assets/
    ├── fonts/
    │   ├── fetch_fonts.py        # regenerates fonts.css + .woff2 files from Google Fonts CSS2 API
    │   ├── fonts.css
    │   └── *.woff2               # self-hosted, latin subset only
    └── logo/
        ├── mark_full.svg         # default mark (≥64px)
        ├── mark_simple.svg       # favicon / small (16–48px)
        ├── mark_mono.svg         # single-color (embroidery, single-ink print)
        ├── wordmark_followthrough.svg        # currentColor, inherits parent text color
        └── wordmark_followthrough_light.svg  # bone-hardcoded, for self-contained dark-surface use
```

## Brand source of truth

The brand system (voice, editorial, visual identity, build pipeline) lives in
`C:\dev\SaaS Business Plan\`. This site inherits its tokens; refinements that
apply brand-wide should fold back into `brand_assets/followthrough_brand.css`
there, not be re-defined here.

## Deploy

Pushes to `main` auto-deploy via Cloudflare Pages. Preview deployments fire on
every branch and PR.

## License

Proprietary. All rights reserved.
