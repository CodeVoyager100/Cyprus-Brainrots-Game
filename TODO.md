# Cyprus Brainrots Game — TODO

Last reviewed: 2026-03-26 (session 4)

---

## Remaining Features

- [ ] **Rarity system** — Add rarity tiers to characters (Common, Rare, Epic, Legendary). Visual presentation in Bazaar. *(deferred — plan upgrade system first)*
- [ ] **Upgrade system** *(depends on rarity)* — Spend coins/XP to upgrade character stats. Based on rarity tier.

---

## Completed

- [x] Persist coins, unlocked characters, selected player and XP via localStorage
- [x] XP system: +1 per kill, +2 for winning, level up every 10 XP
- [x] Animated "Level Up!" message on screen
- [x] XP progress shown in coins panel (e.g. Level 2 · 3/10 XP)
- [x] Fix 3v3 team assignment bug (was 3v1, now correct 3v3)
- [x] Set 3v3 to 6 players, update menu label
- [x] Disable friendly fire for player and AI lasers in team mode
- [x] Fix stationary bot bug (early return before movement code)
- [x] Remove 600px target range cap so bots always find enemies
- [x] Show Red/Blue alive counts in team mode, Players X/Y in showdown
- [x] Team color outline and dot above each player in team modes
- [x] Hide coins display during gameplay, restore on return to menu
- [x] Remove "Game Ready" debug text
- [x] Fix duplicate `handleInputFrame()` — removed dead keyboard-only version, kept joystick version
- [x] Fix `hp`/`currentHp` inconsistency — bot AI now uses `currentHp`
- [x] Remove all `console.log()` calls
- [x] Remove `window.debugGameState` and dead commented-out code blocks
- [x] Scale coin/XP rewards by game mode (3v3 pays more)
- [x] Re-enable health packs — pulsing green cross, player collision, +10 max HP boost per pack
- [x] Auto-healing for player — +1 HP/1.5s after 3s of no damage
- [x] Smarter bots — lead shot, strafe, 40% shoot chance, aim spread at range, wall stop
- [x] Fix bot crash — removed erratic random nudge on wall collision, added gameStarted guard on pack respawn
- [x] Level rewards panel — clickable coins display shows milestone rewards roadmap, auto-claims on level up
