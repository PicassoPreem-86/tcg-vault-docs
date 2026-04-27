# Templates & Layouts

The theme ships with alternate templates for collections and pages. Assign the right template to each collection/page in the admin to get the right layout.

## Assigning a template

**Collections:** Admin → **Products → Collections → [your collection]** → scroll to **Theme template** in the right sidebar → pick from the dropdown.

**Pages:** Admin → **Online Store → Pages → [your page]** → **Theme template** in the right sidebar → pick from the dropdown.

Published themes must have the template file present — if you don't see one in the dropdown, make sure you're on the TCG theme.

## Collection templates

### `collection.game` — Per-game landing
For a collection that holds everything from one TCG (e.g. "MTG", "Pokémon"). Includes:
- Collection banner (image + description)
- Preorder showcase (inline, pulls from this collection)
- Product grid: 4-col portrait, 24/page, filters + sort enabled
- Events list

Assign to: your top-level game collections.

### `collection.set` — Per-set landing
For a collection scoped to a specific set. Includes:
- Collection banner with set image
- Dense 5-col portrait grid, 30/page

Assign to: per-set collections (e.g. "Outlaws of Thunder Junction").

### `collection.preorders` — Preorder showcase
For a preorder-only collection. Includes:
- Banner (no image)
- 3-col square grid with secondary image, 24/page

Assign to: a collection filtered to `tcg.is_preorder = true`.

### `collection.singles` — Dense singles grid
The highest-density layout, for browsing 500–40,000 singles. Includes:
- Minimal banner (no description, no image)
- 5-col portrait grid, 40/page, filters + sort

Assign to: per-game singles collections, bulk singles collections.

### `collection.sealed` — Sealed product
For booster boxes, ETBs, bundles, collection boxes. Includes:
- Collection banner with image
- 4-col square grid, 16/page, secondary image on hover
- Wholesale showcase strip

Assign to: your sealed/booster collections.

### `collection.supplies` — Accessories
For sleeves, binders, playmats, deck boxes. Includes:
- Collection banner with description
- 4-col square grid, 24/page, vendor shown

Assign to: your supplies/accessories collections.

## Page templates

### `page.events` — Events listing
For an in-store events page. Includes:
- Page content (hero text, rules, contact info)
- TCG event list with 6 example events (replace with your own in the theme editor)

Assign to: `/pages/events`.

### `page.buylist` — Buylist landing
For your "we buy cards" page. Includes:
- Page content (how it works, payout terms, hours)
- App section — hosts the buylist app block from BinderPOS / TCG Sync / TCGplayer Pro

Assign to: `/pages/buylist`.

### `page.deckbuilder` — Deckbuilder landing
For a deck-construction tool page. Includes:
- Page content (instructions)
- App section — hosts the deckbuilder app block

Assign to: `/pages/deckbuilder`.

## When to use which grid density

| Product type | Grid | Rationale |
|---|---|---|
| Singles (any game) | 5-col portrait | Cards have a 2.5×3.5 aspect; 5-col keeps images readable at 1200px width |
| Sealed (booster boxes, ETBs) | 4-col square | Packaging varies; square crops show all sides equally |
| Supplies (sleeves, binders) | 4-col square | Consistent square crops; vendor name is important for shoppers |
| Pre-orders | 3-col square | Bigger cells support release-date + countdown pills |
| Per-set landing | 5-col portrait | Same as singles, since sets are usually 200+ singles |
| Per-game landing | 4-col portrait | Mix of singles + sealed; 4-col balances both |

You can override any of these in the theme editor by editing the template's `main-collection-product-grid` section settings.
