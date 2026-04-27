# TCG Sections Reference

The theme ships with nine TCG-specific sections. Each has a preset in the theme editor's **Add section** menu, so you can drop them on any page.

## tcg-game-tiles

Hero grid of game entry points — one tile per TCG you stock, with per-game accent colors.

**Blocks:** one `game_tile` per game (add via Add block → Game tile).

| Setting | Purpose |
|---|---|
| Heading, Heading size | Section title |
| Tile ratio | square / portrait (5:7) / landscape (16:9) |
| Columns (desktop / mobile) | Grid density |
| Per-block: game_name, image, accent_color, link | Tile content |

Use on: homepage, collection list page.

## tcg-game-mega-menu

Header-group section — horizontal tab bar per game that expands into a mega-panel of linklist items. Place this in the **header section group** alongside announcement bar + header.

**Blocks:** one `game` per game (up to 10).

| Setting | Purpose |
|---|---|
| Per-block: game_name, accent_color, game_link | Tab label + underline color + shop-all link |
| Per-block: tagline | Short line shown in the expanded panel |
| Per-block: menu | Shopify linklist for this game's sub-nav |

Use on: header group. See [Game Mega-Menu](mega-menu.md) for setup.

## tcg-preorder-showcase

Grid of preorder products with release-date badges and countdown pills.

| Setting | Purpose |
|---|---|
| Collection | Source collection (filter to `tcg.is_preorder=true` via Shopify collection rules) |
| Products to show | 2–12 |
| Show release date | Display the formatted date under each product |
| Show countdown | "Ships in N days" pill when within threshold |
| Countdown threshold (days) | When to start showing the countdown (7–97) |
| Image ratio | square / portrait / landscape |

Reads `tcg.release_date` from each product.

Use on: homepage, game landing pages, preorder collection template.

## tcg-singles-grid

Dense featured singles grid — denser than the default featured-collection, tuned for cards.

| Setting | Purpose |
|---|---|
| Collection | Source collection |
| Products to show | 4–20 |
| Columns (desktop / mobile) | 3–6 desktop, 2 mobile |
| Show badges | Set code + rarity dot per card |
| Show meta | Set name / card number |

Reads `tcg.set_code`, `tcg.set_name`, `tcg.card_number`, `tcg.rarity`.

Use on: homepage, game landing pages.

## tcg-supplies-grid

Product grid tuned for accessories — square thumbnails, vendor shown.

| Setting | Purpose |
|---|---|
| Collection | Source collection |
| Products to show | 2–12 |
| Columns (desktop / mobile) | 2–5 desktop, 2 mobile |
| Show vendor | Display brand under each product |

Use on: homepage, supplies collection template.

## tcg-event-list

Events listing (FNM, pre-releases, tournaments, leagues). Each event is a block — no external data source required.

**Blocks:** one `event` per event.

| Per-block setting | Purpose |
|---|---|
| title | Event name |
| event_date | YYYY-MM-DD |
| time | Display string (e.g. "7:00 PM") |
| game | Optional game badge |
| format | Optional format badge (Draft / Commander / etc.) |
| location | "In-store" or a link |

Use on: homepage, events page (`page.events.json` template).

## tcg-specials-banner

Weekly specials / sale banner with optional countdown.

| Setting | Purpose |
|---|---|
| Kicker | Small label above heading (e.g. "WEEKLY SPECIALS") |
| Heading, subheading | Body copy |
| End date | Optional — shows countdown |
| Button label / link (×2) | Primary + secondary CTAs |
| Alignment | flex-start / center / flex-end |

Use on: homepage, above-fold promo slot.

## tcg-free-shipping-bar

Slim "Orders $X+ ship free" bar. Can be static or progress-tracking against cart total.

| Setting | Purpose |
|---|---|
| Message | Supports `{threshold}` placeholder |
| Threshold amount | Dollar amount |
| Show icon | Truck icon |
| Text size | 1–3 |

Use on: top of homepage, above header, cart drawer.

## tcg-wholesale-showcase

Bulk/case products for resellers — elevated card style with case-quantity emphasis.

| Setting | Purpose |
|---|---|
| Collection | Source collection (filter to your wholesale/cases collection) |
| Products to show | 2–6 |
| Show description | Display product description snippet |
| Columns desktop | 2–4 |
| Kicker, heading, subheading | Section intro |

Use on: homepage, dedicated `/pages/wholesale` page, sealed collection template.
