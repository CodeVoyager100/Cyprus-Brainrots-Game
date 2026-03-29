# Cyprus Brainrots Game — TODO

Last reviewed: 2026-03-29 (session 7)

---

## Remaining Features

### Easy
- [ ] **Settings menu** — Volume slider, toggle joystick visibility, maybe keybinds *(UI panel + a few variables)*
- [ ] **Emotes/taunts** — Press a key to display a short emote above your character *(key handler + draw text bubble)*
- [ ] **Sound effects per character** — Unique shoot/death sounds for each brainrot character *(add sound file refs to `playersData`, play on shoot/death)*

### Medium
- [x] **Medal system** *(replaces XP)* — Rename XP to Medals (🏅); win = +medals, lose = −medals (like Brawl Stars trophies). Rank based on medal count instead of flat XP *(rework awardXP → awardMedals, update UI/localStorage, add medal loss on defeat)*
- [ ] **Star drops** — Post-match reward chest; after winning (or losing?) a match you open a star drop that contains a random reward (coins, character unlock, etc.) *(new end-screen UI + reward pool logic)*
- [ ] **Rarity system** — Add rarity tiers to characters (Common, Rare, Epic, Mythic, Legendary). Visual presentation in Bazaar *(data + UI, no new game logic)*
- [ ] **Gadgets** — One-time-use ability per match per character (e.g. dash, shield, heal burst, teleport). Activated by a button/key *(new ability system, UI button, cooldown tracking)*
- [ ] **Bounty mode** — Kills give stars; team with most stars when timer ends wins *(new win condition + timer + star tracking HUD)*

### Hard
- [ ] **Super ability** — Each character charges a special attack by dealing damage (e.g. Tornader → tornado AoE, Lazerman → piercing beam, Fournakis → fire zone). Bar fills up, press key to unleash *(per-character super definitions, charge meter, new projectile/AoE rendering + collision)*
- [x] **Poison gas / shrinking zone (Showdown)** — Map slowly shrinks with a damage zone pushing players inward *(zone boundary rendering, periodic damage tick, timer system)*
- [x] **Ball-Goal mode** — Soccer-style: kick a ball into the enemy team's goal to score. First to 2 goals wins *(ball physics, goal zones, score tracking, reset on goal)*
- [ ] **Respawn system (team modes)** — When you die in 3v3/2v2, spectate your teammate; if they survive 15 seconds you respawn next to them *(spectate camera, timer, safe-position check)*
- [ ] **Unique attacks per character** — Some characters get non-laser attacks (e.g. spread shot, boomerang, area blast, homing projectile) *(new projectile types, new rendering + collision logic per character)*
- [ ] **Upgrade system** *(depends on rarity)* — Spend coins/medals to upgrade character stats. Based on rarity tier *(depends on rarity system)*

### Hardest
- [ ] **Account system** — Username + password login, persist coins/medals/unlocks server-side (or localStorage profile switcher as a simpler first step) *(requires a backend or significant auth flow)*

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
- [x] 2v2 game mode — added UI card + fixed maxPlayers (8→4) for correct 2v2 teams
- [x] 4-team system — added Green and Yellow teams to 3v3 (12 players) and 2v2 (8 players); last team standing wins
- [x] Bushes — green cover zones near walls/lakes; players inside are invisible to enemies; bots seek bushes when low HP
- [x] Team spawn separation — each team spawns in a different map quadrant (red=NW, blue=NE, green=SW, yellow=SE)
- [x] Bush stealth break — shooting or taking damage reveals you from bush for ~1.5s; bushes are now square
- [x] Medal system — replaced XP with Medals (🏅); win = +medals, lose = −medals; level based on total medals
- [x] Poison gas zone (Showdown) — purple shrinking safe zone in 5 phases; increasing damage outside; pulsing visual + warning text
- [x] Ball-Goal mode — 3v3 soccer: kick ball into opponent's goal, first to 2 scores wins; bot ball-chasing AI; score HUD
