# FAQ & Troubleshooting

## General

### Which TCGs does the theme support?
Any of them. The theme is game-agnostic — you decide which games to stock, label, and surface. Game-specific defaults are provided for MTG, Pokémon, Yu-Gi-Oh!, One Piece, Lorcana, Star Wars Unlimited, Flesh and Blood, Digimon, Dragon Ball Super, Final Fantasy TCG, Union Arena, Gundam, Riftbound, Altered, and Sorcery.

### Do I have to use the `tcg.*` metafields?
No. Every TCG-specific block hides gracefully when its source metafields/variants are empty. You can ship the theme with standard Shopify data and layer in the TCG metafields as you're ready.

### Does the theme require an inventory app?
No. The theme hosts app blocks from BinderPOS, TCGplayer Pro, TCG Sync, Crystal Commerce, and similar, but doesn't depend on any of them. Manually-managed conditions + metafields work identically.

## Product pages

### My condition-price block is empty
Two things to check:
1. The product has a variant option named exactly **Condition** (or whatever you set the block's **Variant option name** to).
2. The condition values on the product match the block's **Condition values to show** setting (case-insensitive). E.g. a variant called "NM" won't match "Near Mint" — either rename the variant or update the block.

### My stock indicator shows 0 even though I have stock
The indicator reads `inventory_quantity`, which only populates when **Track quantity** is enabled on the variant and inventory is set to **Shopify**. Products with `inventory_management: nil` always show 0.

### My foil/finish badge isn't showing
- Is `tcg.finish` set on the product?
- Is the value one of: `foil`, `etched`, `holo`, `reverse_holo`, `reverse`?
- Is it `normal` or empty? Those intentionally hide the badge.

### My buylist price block is empty
Verify:
1. The metafield exists on the product (**Custom data → Products**).
2. The metafield is type **money** — other types may not format correctly.
3. The block's **Metafield namespace** and **Metafield key** match exactly (case-sensitive).

## Collections

### Filters aren't showing my TCG fields
Shopify collection filters read from product tags, product type, variant options, and approved metafield namespaces. To filter by `tcg.game` or `tcg.rarity`:
1. **Settings → Custom data → Products** → find each metafield.
2. Under **Storefront access**, enable **Use as a filter**.
3. **Settings → Markets → [market] → Catalog → Filters** → add the metafield as a filter.

## Mega-menu

### Panels aren't expanding
Check the browser console for JavaScript errors. The mega-menu uses a custom element `<tcg-mega-menu>` — if the script didn't load, panels won't open. Reload the page, and if it persists, confirm the theme assets loaded (look for a 404 in the Network tab).

### Panel shows empty
The linklist is empty or unassigned on that game block. In the theme editor, open the block and pick a linklist under **Sub-nav linklist**.

### Sub-nav doesn't show columns
The linklist needs 2 levels — top-level items with children. A flat linklist (no children) renders as a single list without column headings.

## Performance

### Theme feels slow on mobile
1. Check image sizes. Products with 20+ uploaded images slow LCP. Use the image focal point + Shopify's built-in responsive sizing.
2. Keep homepage sections under 8. Each section adds weight.
3. If you added custom apps, each app block loads its own JS — remove ones you don't need.

### My Lighthouse score dropped
Sections like `tcg-preorder-showcase` and `tcg-wholesale-showcase` load products at render time. A collection with 1000 products + `products_to_show: 12` is light; a collection with 10,000 products can degrade LCP. Point the section at a focused collection (e.g. "Featured Preorders" instead of "All").

## Apps & integrations

### Switching from another TCG theme — will my data come over?
Variants, products, collections, customer data, and standard metafields transfer automatically (they live on the Shopify side). You'll need to:
1. Create the `tcg.*` metafield definitions if they don't already exist.
2. Populate them via CSV import or app sync.
3. Reassign custom templates per collection/page in the admin.

### Can I use this theme with Shopify Markets?
Yes — the theme supports country/language selectors and Markets-aware pricing.

## Customization

### Can I add my own game accent colors?
Yes. Each `tcg-game-tiles` and `tcg-game-mega-menu` block has an **Accent colour** picker. For theme-wide custom tokens, edit `assets/component-tcg-product.css` or add overrides in `snippets/` — those are standard Liquid/CSS edits.

### Can I change the card condition names?
Yes. Add variant option values with whatever names you prefer (e.g. "Pack Fresh" instead of "Near Mint"), then update the **Condition values to show** setting on the relevant blocks to match.

### Can I hide the TCG blocks on a specific product?
Yes. Create a secondary `product.alt.json` template without those blocks, then assign it to the product (**Products → [product] → Theme template → product.alt**).

## Still stuck?

Email support: *(your support email here)*
Help desk: *(your help desk URL here)*
