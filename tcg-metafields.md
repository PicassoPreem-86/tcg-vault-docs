# TCG Metafield Namespace

The TCG Theme uses a dedicated `tcg.*` metafield namespace to drive card-specific displays — set names, conditions, rarities, finishes, preorder dates, and more. These metafields are **optional**: the theme gracefully falls back to standard Shopify product data when they're not set.

Metafield definitions can be created once in your Shopify admin (**Settings → Custom data → Products → Add definition**) and then populated per product — manually, via CSV import, or automatically by your TCG inventory app (BinderPOS, TCGplayer Pro, TCG Sync, etc.).

## Definitions

| Key | Type | Required | Example | Displays where |
|-----|------|----------|---------|----------------|
| `tcg.game` | Single line text | No | `MTG` | Product badge, filter |
| `tcg.set_code` | Single line text | No | `OTJ` | Product badge |
| `tcg.set_name` | Single line text | No | `Outlaws of Thunder Junction` | Product page, collection |
| `tcg.card_number` | Single line text | No | `142/276` | Product page |
| `tcg.rarity` | Single line text | No | `Mythic Rare` | Product badge |
| `tcg.color_type` | List (single line text) | No | `["Red", "Black"]` | Product page, filters |
| `tcg.artist` | Single line text | No | `Rebecca Guay` | Product page |
| `tcg.finish` | Single line text | No | `foil` | Product badge |
| `tcg.release_date` | Date | No | `2026-04-12` | Preorder section, countdown |
| `tcg.is_preorder` | Boolean | No | `true` | Preorder section filter |
| `tcg.format_legality` | List (single line text) | No | `["Modern", "Commander"]` | Collection filter |

## Recommended `tcg.format_legality` values

MTG-only. Use these canonical strings for consistency across filters:

- `Standard`, `Pioneer`, `Modern`, `Legacy`, `Vintage`, `Commander`, `Pauper`, `Brawl`

Non-MTG games (Pokémon, YGO, One Piece, Lorcana) do not use this field.

## Recommended `tcg.game` values

Use these canonical codes for consistency across collections and filters:

| Code | Game |
|------|------|
| `MTG` | Magic: The Gathering |
| `POKEMON` | Pokémon TCG |
| `YGO` | Yu-Gi-Oh! |
| `OP` | One Piece Card Game |
| `LORCANA` | Disney Lorcana |
| `SWU` | Star Wars Unlimited |
| `FAB` | Flesh and Blood |
| `DIGIMON` | Digimon Card Game |
| `DBS` | Dragon Ball Super |
| `FFTCG` | Final Fantasy TCG |
| `UNION` | Union Arena |
| `GUNDAM` | Gundam Card Game |
| `RIFTBOUND` | Riftbound |
| `ALTERED` | Altered |
| `SORCERY` | Sorcery: Contested Realm |

Merchants stocking other games can add their own codes — the theme treats `tcg.game` as an opaque string for branding and filtering.

## Recommended `tcg.finish` values

| Value | Meaning |
|-------|---------|
| `normal` | Standard print (default if unset) |
| `foil` | Traditional foil |
| `etched` | Etched foil (MTG) |
| `reverse_holo` | Reverse holographic (Pokémon) |
| `holo` | Holographic |
| `first_edition` | First edition (YGO, Pokémon) |
| `alt_art` | Alternate art |
| `borderless` | Borderless / extended art |

## Recommended `tcg.rarity` values

Rarity varies by game. Use the game's own convention — the theme renders the string verbatim:

- **MTG:** `Common`, `Uncommon`, `Rare`, `Mythic Rare`
- **Pokémon:** `Common`, `Uncommon`, `Rare`, `Holo Rare`, `Ultra Rare`, `Secret Rare`
- **YGO:** `Common`, `Rare`, `Super Rare`, `Ultra Rare`, `Secret Rare`, `Ghost Rare`
- **One Piece:** `C`, `UC`, `R`, `SR`, `SEC`, `L`
- **Lorcana:** `Common`, `Uncommon`, `Rare`, `Super Rare`, `Legendary`, `Enchanted`

## Preorders

Mark a product as a preorder by setting **both**:
- `tcg.is_preorder` → `true`
- `tcg.release_date` → the expected ship date

The theme's preorder sections will automatically surface these products, sort by release date, and display a countdown when the date is within 60 days.

## Inventory-App-Managed Metafields

If you use a TCG inventory app (BinderPOS, TCGplayer Pro, TCG Sync, Crystal Commerce), it likely populates condition-based variants and pricing through its own metafield namespace (e.g., `tcgplayer.*` or `binderpos.*`). The TCG Theme doesn't overwrite those — instead, it hosts app blocks from the app in condition-aware sections on your product pages.

The `tcg.*` namespace above is for **product-level catalog data** that's stable across inventory tools.
