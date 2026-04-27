# Getting Started

This guide gets your TCG store live on the theme in under 30 minutes.

## 1. Install the theme

1. From the Shopify admin, go to **Online Store → Themes**.
2. Click **Add theme** → **Upload zip file** and upload the TCG Theme ZIP.
3. Once uploaded, click **Customize** to open the theme editor.

The theme is published only when you click **Publish** on the theme card. Until then, it runs as an unpublished theme and doesn't affect your live store.

## 2. Choose your preset

The theme ships with two presets:

| Preset | For | Look |
|---|---|---|
| **Vault** | Singles-first shops scaling from 50 to 50,000+ cards | Dark, dense, product-data-forward |
| **Sealed** | Sealed + supplies shops (11–100+ SKUs) | Light, airier, product-hero |

To switch preset: in the theme editor, click **Theme settings** → **Presets**, then pick Vault or Sealed. Switching presets rewrites your color schemes, card styles, typography, and cart type, but **does not** touch your product data or section content.

## 3. Set up the `tcg.*` metafield namespace

The theme reads per-product card data from a `tcg.*` metafield namespace (set name, rarity, finish, release date, etc.). Define these once in your admin so they're available on every product:

1. Go to **Settings → Custom data → Products**.
2. Click **Add definition** and create each of the metafields listed in [TCG Metafields](tcg-metafields.md).
3. Save.

You don't have to populate every field on every product — the theme hides any TCG block whose metafields are empty.

## 4. Set up condition variants (singles shops only)

If you sell singles with condition tiers (NM/LP/MP/HP/DMG):

1. Open a product in the admin.
2. Under **Variants**, add an option named exactly **Condition**.
3. Set the option values to your condition labels: **Near Mint**, **Lightly Played**, **Moderately Played**, **Heavily Played**, **Damaged**.
4. Set prices and inventory per variant.

The theme's **TCG condition price tiers** and **TCG stock indicator** product blocks will auto-populate from these variants. See [Product Pages](product-pages.md) for full details.

## 5. Configure the game mega-menu

If you want the per-game header nav:

1. Go to **Online Store → Navigation** and create one linklist per game (e.g. `mtg-menu`, `pokemon-menu`, `ygo-menu`).
2. Each linklist should be 2-level: top-level items (Singles / Sealed / Supplies / Pre-Orders) with child links (specific sets).
3. In the theme editor, open the header section group.
4. Add the **TCG game mega-menu** section.
5. For each game block, select the matching linklist.

See [Game Mega-Menu](mega-menu.md) for a worked example.

## 6. Customize per-game accent colours

Each TCG game can have its own accent colour, used on game tiles and the mega-menu. Defaults ship with:
- MTG `#C9A227`
- Pokémon `#E3350D`
- Yu-Gi-Oh! `#6B3FA0`
- One Piece `#D4333F`
- Lorcana `#7A5FB8`
- Star Wars Unlimited `#2B3A55`

Change these in each game block's settings in the theme editor.

## 7. Connect your TCG inventory app (optional)

If you use BinderPOS, TCGplayer Pro, TCG Sync, Crystal Commerce, or similar, the theme hosts their app blocks on the product page, cart drawer, buylist page, and deckbuilder page.

See [App Integrations](apps.md) for per-app setup.

## 8. Before you publish

Run the theme preview (click the **eye** icon in the theme editor) and check:
- [ ] Homepage shows all TCG sections populated
- [ ] At least one product has TCG metafields filled in and shows the badges/metadata/condition blocks
- [ ] Mega-menu hovers expand correctly
- [ ] The cart/checkout work end-to-end
- [ ] Mobile layout looks right (use the mobile preview toggle)

When ready, click **Publish** on the theme in **Online Store → Themes**.
