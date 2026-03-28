# Cyprus Brainrots Game — TODO

Last reviewed: 2026-03-27 (session 5)

---

## Remaining Features

<!-- ordered easiest → hardest -->

- [x] **Kill feed** — Small scrolling log in the corner showing who killed who *(easy: just track kill events and draw text)*
- [x] **Leaderboard screen** — End-of-game scoreboard showing kills, damage dealt, healing received *(easy: collect stats already in game state, show on game end)*
- [ ] **Settings menu** — Volume slider, toggle joystick visibility, maybe keybinds *(easy: UI panel + a few variables)*
- [ ] **Emotes/taunts** — Press a key to display a short emote above your character *(easy: key handler + draw text bubble)*
- [ ] **Sound effects per character** — Unique shoot/death sounds for each brainrot character *(easy: add sound file refs to `playersData`, play on shoot/death)*
- [ ] **2v2 game mode** — Same rules as 3v3 but 2 players per team (1 human + 1 bot vs 2 bots); add to mode select menu *(medium: copy 3v3 config, adjust player count)*
- [ ] **Star drops** — Post-match reward chest; after winning (or losing?) a match you open a star drop that contains a random reward (coins, character unlock, etc.) *(medium: new end-screen UI + reward pool logic)*
- [ ] **Rarity system** — Add rarity tiers to characters (Common, Rare, Epic, Mythic, Legendary). Visual presentation in Bazaar *(medium: data + UI, no new game logic)*
- [ ] **Respawn system (team modes)** — When you die in 3v3/2v2, spectate your teammate; if they survive 15 seconds you respawn next to them (safe spawn, not inside a wall) *(hard: spectate camera, timer, safe-position check)*
- [ ] **Unique attacks per character** — Some characters get non-laser attacks (e.g. spread shot, boomerang, area blast, homing projectile) *(hard: new projectile types, new rendering + collision logic per character)*
- [ ] **Upgrade system** *(depends on rarity)* — Spend coins/XP to upgrade character stats. Based on rarity tier *(hard: depends on rarity system)*
- [ ] **Account system** — Username + password login, persist coins/XP/unlocks server-side (or localStorage profile switcher as a simpler first step) *(hardest: requires a backend or significant auth flow)*

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
