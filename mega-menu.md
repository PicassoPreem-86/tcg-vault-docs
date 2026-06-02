---
title: "Game Mega-Menu Setup"
---

# Game Mega-Menu Setup

The `tcg-game-mega-menu` section is a horizontal nav bar with a tab per TCG you carry, each of which expands into a mega-panel showing that game's sub-navigation organized into columns. This guide walks through setting it up end-to-end.

## 1. Create a linklist per game

Shopify linklists (**Online Store → Navigation**) drive the sub-nav. You want one linklist per game.

For each game:

1. **Online Store → Navigation** → **Add menu**.
2. Give it a clear name, e.g. `MTG Menu`. The **handle** auto-generates (e.g. `mtg-menu`).
3. Add top-level items — each becomes a **column heading** in the mega-panel. Recommended columns:
   - Singles
   - Sealed
   - Pre-Orders
   - Featured Sets
   - Supplies
4. Under each top-level item, add children — these become **links in that column**.

Example for an MTG linklist:

```
MTG Menu
├── Singles
│   ├── Standard
│   ├── Modern
│   ├── Commander
│   └── Legacy
├── Sealed
│   ├── Booster Boxes
│   ├── Bundles
│   └── Collector Boxes
├── Pre-Orders
│   ├── Upcoming Set A
│   └── Upcoming Set B
└── Featured Sets
    ├── Current Standard set
    ├── Recent release 1
    └── Recent release 2
```

Repeat for each game. You can skip games you don't carry.

## 2. Add the mega-menu section to the header group

1. In the theme editor, click the **header section group** in the sidebar.
2. Click **Add section** → **TCG game mega-menu**.
3. The section is placed at the bottom of the header group. Drag it above or below the main header as you prefer — many shops place it directly below the header.

## 3. Configure each game tab

The section ships with 6 default game blocks (MTG, Pokémon, YGO, One Piece, Lorcana, SWU). For each block:

| Field | What to set |
|---|---|
| **Game name** | Display name (e.g. "Magic: The Gathering") |
| **Accent colour** | Tab underline + link hover color (see defaults in [Getting Started](getting-started.html)) |
| **Shop-all link** | Top-level link, e.g. your game collection (`/collections/mtg`) |
| **Tagline** | Short line shown in the expanded panel (e.g. "Singles, sealed, and pre-orders") |
| **Sub-nav linklist** | The linklist you created in step 1 |

Remove blocks for games you don't stock, or add new ones with **Add block → Game** (up to 10).

## 4. Ordering

Order games left-to-right by volume or priority. The tabs horizontally scroll on narrow viewports, so prioritize your top sellers.

## Accessibility

The mega-menu is keyboard-navigable:
- **Tab** moves focus through tabs
- **Enter/Space** toggles a panel
- Focus a tab to auto-open its panel
- **Escape** closes the open panel
- Clicking outside the nav closes the open panel

The section sets an appropriate `aria-label` on the nav container, toggles `aria-expanded` on each tab, and connects each tab to its panel via `aria-controls`.
