# Product Pages

The theme's product page is built around **six TCG-specific blocks** that read from a combination of product variants and the `tcg.*` metafield namespace. Each block hides itself gracefully when its data source is empty, so you can use the same product template for singles, sealed, and supplies without customizing per SKU type.

## The six TCG product blocks

| Block | Reads from | Displays |
|---|---|---|
| **TCG set + rarity badge** | `tcg.set_code`, `tcg.rarity` | Set pill (e.g. `OTJ`) + rarity dot (color-coded) |
| **TCG foil/finish badge** | `tcg.finish` | Foil/etched/holo/reverse badge with iridescent treatment |
| **TCG condition price tiers** | Product variants named **Condition** | Lowest price per condition (NM/LP/MP/HP/DMG) |
| **TCG stock indicator** | Product variants named **Condition** | Summed inventory per condition, amber low-stock highlight |
| **TCG card metadata** | `tcg.game`, `tcg.set_name`, `tcg.set_code`, `tcg.card_number`, `tcg.rarity`, `tcg.color_type`, `tcg.artist` | Definition list — Game · Set · Rarity · Color · Artist |
| **TCG buylist price** | Configurable app metafield (default `buylist.price`) | Sell-to-us price + optional "Sell yours" CTA link |

All six are included in the default `product.json` template. Remove, reorder, or duplicate in the theme editor (one instance per page max).

## Setting up condition variants

The condition-price and stock-indicator blocks read from a **variant option** named `Condition`. To set this up on a product:

1. Open the product in the admin.
2. **Variants** section → click **Add options like size or color**.
3. Option name: `Condition`
4. Option values (add each one separated by comma): `Near Mint, Lightly Played, Moderately Played, Heavily Played, Damaged`
5. Save — a variant is created per condition.
6. Set a price and an inventory quantity per variant.

You can rename "Condition" to anything (e.g. "Grade") — just update the **Variant option name** setting on the two blocks to match.

### Customizing which conditions appear

The blocks have a **Condition values to show** setting (comma-separated). The default is all 5 grades:

```
Near Mint,Lightly Played,Moderately Played,Heavily Played,Damaged
```

If you only stock NM/LP, set it to `Near Mint,Lightly Played` and the others won't render.

The stock indicator also has a **Low-stock threshold** slider (default 3) — any condition with ≤3 in stock renders in amber.

## Buylist pricing

The buylist price block reads from any product metafield. Default: `buylist.price`.

If your buylist app (BinderPOS, TCG Sync) writes the buy price to a different metafield, update the block's **Metafield namespace** and **Metafield key** settings. The metafield must be a **money** type for correct formatting.

Optional: set a **CTA label** (default "Sell yours") and **CTA link** pointing to your buylist page (e.g. `/pages/buylist`).

## Rarity badge colors

The rarity dot is color-coded by the first word of your `tcg.rarity` metafield value:

| First word | Dot color |
|---|---|
| Common | gray |
| Uncommon | silver |
| Rare / Holo | gold |
| Mythic | orange |
| Super / Ultra | purple / pink |
| Secret | deep purple |
| Legendary / Enchanted | yellow / pink |
| Promo | cyan |

For example: `Mythic Rare`, `Holo Rare`, and `Ultra Rare` are all recognized. Unknown rarity phrases render with a neutral dot — they still show the rarity text.

## Foil/finish badge values

The foil/finish badge has styled treatments for these `tcg.finish` values:

| Value | Treatment |
|---|---|
| `foil` | Full iridescent shimmer |
| `etched` | Gold-etched gradient |
| `holo` | Holographic shimmer |
| `reverse_holo` / `reverse` | Pastel reverse-holo gradient |

Any other value (including `normal` or empty) hides the badge.

## Product template structure

The default `product.json` block order:

1. Vendor
2. Title
3. Caption (subtitle metafield)
4. TCG set + rarity badge
5. TCG foil/finish badge
6. Price
7. TCG condition price tiers
8. TCG stock indicator
9. Variant picker
10. Quantity selector
11. Buy buttons
12. Description
13. TCG card metadata
14. TCG buylist price
15. Collapsible: Condition Guide (pre-populated)
16. Collapsible: Shipping & Returns
17. Collapsible: About This Set
18. Share

Every block is optional — drag to reorder or remove in the theme editor.
