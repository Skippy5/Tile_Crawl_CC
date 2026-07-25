# Tile Crawl CC

A complete solo tile-laying dungeon crawler in a single self-contained HTML file — in the tradition of *Bag of Dungeon* and *Book of Dungeons*. Vanilla JS, no frameworks, no build step, no external assets, no storage. Open `index.html` and play.

**Play it:** create a hero, descend the stair, reveal the dungeon tile by tile, find the Vault, take the Ember Crown from the Bone Tyrant, and get back to the stair alive.

## How it plays

- **Four classes** — Warrior, Rogue, Mage, Cleric — each with its own stats, weapon, and kit.
- **Tile-laying map** — every move draws one of 16 tiles from a shuffled deck; rotate it so a doorway lines up, place it, and roll a d12 for what's inside: monsters, treasure, traps, items, shrines, a guarded hoard — or the Vault itself.
- **A physical dice tray** — d4 through d20, each a distinct shape. Drag and release to throw (drag distance sets the tumble), or click for a gentle roll. The game *never* rolls for you — you throw the monsters' dice too.
- **Turn-based combat** — attack, class powers, items, or flee (fled monsters wait for you). Natural 20s crit for double damage dice.
- **The dungeon knows** — carrying the Crown shifts every monster roll one step harder on the table.

It is a hard, push-your-luck game. Death is quick and the New Run button is right there.

## Code layout (for extending)

All game data lives in top-level tables at the top of the script — `CONFIG`, `CLASSES`, `TILES`, `MONSTERS`, `ITEMS`, `EVENTS`, `TRAPS`, `ROOM_TABLE`. Adding a monster or item is a one-object append. A single `state` object with an explicit phase machine (`create → explore → placing → rolling → combat → dead/won`) drives one `render()`; rules helpers (`rollDie`, `rotateExits`, `canConnect`) are pure functions kept apart from rendering. Extension seams are commented at the bottom of the script (floors, leveling, shops).

---

Built with Claude Code.
