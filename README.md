# TCG Vault — Theme Documentation

Public merchant documentation for the **TCG Vault** Shopify theme. This repo is
the **public docs site only** — the theme source lives in a separate private repo.
Published via GitHub Pages at:

**https://picassopreem-86.github.io/tcg-vault-docs/**

This URL is referenced in the Theme Store listing and reviewer instructions, so
the repo must be named exactly `tcg-vault-docs` under the `PicassoPreem-86` account.

## One-time setup

1. Create a **public** repo named `tcg-vault-docs` under `PicassoPreem-86`
   (do not initialize with a README/license — this repo already has them).
2. From this directory, push:
   ```bash
   git push -u origin main
   ```
   (`origin` is already set to `https://github.com/PicassoPreem-86/tcg-vault-docs.git`.)
3. In the repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. The `Deploy Jekyll docs to GitHub Pages` workflow runs on push; wait ~1–2 min,
   then confirm the site loads at the URL above.

## Local preview (optional)

```bash
bundle install
bundle exec jekyll serve
# open http://localhost:4000/tcg-vault-docs/
```

## Contents

Purpose-built theme for Trading Card Game retailers on Shopify. Two presets —
**Vault** (dark, singles-first) and **Sealed** (light, sealed+supplies-first) —
both driven by the same `tcg.*` metafield namespace and app-block mount points.

1. **[Getting Started](getting-started.md)** — install, choose a preset, essential setup
2. **[TCG Metafields](tcg-metafields.md)** — the `tcg.*` namespace that drives card displays
3. **[Product Pages](product-pages.md)** — condition variants, TCG blocks, buylist pricing
4. **[Sections Reference](sections.md)** — every TCG-specific section and how to configure it
5. **[Game Mega-Menu](mega-menu.md)** — header nav with per-game linklists
6. **[Templates & Layouts](templates.md)** — the TCG-specific collection/page templates
7. **[App Integrations](apps.md)** — BinderPOS, TCGplayer Pro, TCG Sync, Crystal Commerce, SortSwift
8. **[Preset Differences](presets.md)** — Vault vs Sealed: what changes, when to switch
9. **[FAQ & Troubleshooting](faq.md)** — common questions, gotchas, fixes

## Support

- **Email:** dean@bknddevelopment.com
- **Help desk:** https://tawk.to/tcgvault

## Theme Requirements

- Shopify Online Store 2.0
- No additional apps required (the theme hosts app blocks from your existing TCG inventory tools)

## License

Documentation © BKND Development. The TCG Vault theme is sold separately under its own license.
