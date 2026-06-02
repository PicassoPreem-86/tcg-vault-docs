---
title: "App Integrations"
---

# App Integrations

The theme **doesn't depend on any specific TCG app** (Shopify Theme Store rules prohibit that), but it's built as a great **host** for the common TCG inventory and buylist apps. This guide shows where app blocks can mount and how to integrate each major TCG app.

## Where app blocks mount in the theme

The theme exposes `@app` block support in these places:

| Location | Section | Purpose |
|---|---|---|
| Product page | `main-product` | Condition variants, variant swatches, inventory by condition |
| Featured product | `featured-product` | Same blocks on homepage product showcases |
| Buylist page | `apps` (via `page.buylist.json`) | Full buylist app |
| Deckbuilder page | `apps` (via `page.deckbuilder.json`) | Full deckbuilder app |
| Any page/template | `custom-liquid` blocks | App tokens, custom widgets |

Add app blocks via the theme editor: **Add block → Apps** inside any of the above sections.

## Per-app setup

### BinderPOS

BinderPOS handles POS + buylist + condition-based inventory.

1. Install BinderPOS from the Shopify App Store.
2. Go to your product page in the theme editor → **Main product** section → **Add block → Apps** → pick the BinderPOS block.
3. For the buylist page (`/pages/buylist`):
   - Set the template to `page.buylist`.
   - In the theme editor, open that page → **Apps** section → **Add block → Apps** → BinderPOS buylist.
4. BinderPOS writes condition-based inventory to variants it manages. The theme's **TCG condition price tiers** and **TCG stock indicator** blocks read directly from those variants — no extra config needed as long as BinderPOS uses "Condition" as the option name (it does by default).
5. BinderPOS buylist prices write to a metafield. Configure the theme's **TCG buylist price** block:
   - Metafield namespace: `binderpos` (verify in BinderPOS settings)
   - Metafield key: `buylist_price`

### TCGplayer Pro

TCGplayer Pro syncs condition-based pricing from TCGplayer's marketplace.

1. Install TCGplayer Sync from the Shopify App Store.
2. In TCGplayer Pro settings, enable Shopify variant sync — it creates variants with a "Condition" option.
3. The TCG condition-price and stock-indicator blocks work out of the box.
4. No app block required for basic sync (it writes to variants), but the app may offer additional widgets — add them via **Add block → Apps**.

### TCG Sync

TCG Sync handles both inventory and buylist.

1. Install TCG Sync from the Shopify App Store.
2. TCG Sync uses "Condition" variants by default — no config needed.
3. Buylist metafield is `tcg_sync.buy_price`. Update the **TCG buylist price** block's namespace/key to match.

### Crystal Commerce

Crystal Commerce integrates with Shopify via export/sync.

1. Follow Crystal Commerce's Shopify sync docs.
2. Crystal Commerce exports condition variants similar to BinderPOS.
3. Their buylist metafield is `crystal.buylist_price` — update the **TCG buylist price** block.

### SortSwift, Card Dealer Pro, others

Any app that:
- Manages condition variants via Shopify's native option system
- Writes buylist prices to a product metafield

…will work with the TCG theme without code changes. Just update the block metafield keys to match.

## Not using an app?

You can manage condition variants and buylist pricing manually:

- **Conditions:** add a variant option called "Condition" with your preferred values per product.
- **Buylist pricing:** define a product metafield (e.g. `buylist.price`, money type) and enter values manually.

The theme treats manually-entered metafield data identically to app-written data.

## Inventory across condition variants

The **TCG stock indicator** block reads `inventory_quantity` directly from each variant. For this to work:

1. In the admin, each variant's **Track inventory** must be set to **Shopify**.
2. Set the stock count per variant.

If inventory isn't tracked (or the policy is `continue` for out-of-stock), the block shows `0` — you may want to hide the block for those products or switch the block's **Low-stock threshold** accordingly.

## App-block compatibility matrix

| App | Condition variants | Buylist price block | Custom product blocks | Buylist page | Deckbuilder |
|---|---|---|---|---|---|
| BinderPOS | ✓ | `binderpos.buylist_price` | ✓ | ✓ | — |
| TCGplayer Pro | ✓ | — | ✓ | — | — |
| TCG Sync | ✓ | `tcg_sync.buy_price` | ✓ | ✓ | — |
| Crystal Commerce | ✓ | `crystal.buylist_price` | ✓ | partial | — |
| Card Dealer Pro | ✓ | `cdp.buylist_price` | ✓ | ✓ | — |
| SortSwift | ✓ | — | ✓ | — | — |

**Verify the exact metafield keys in each app's settings** — vendors occasionally change them.
