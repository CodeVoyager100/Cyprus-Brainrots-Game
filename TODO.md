# Cyprus Brainrots Game — TODO

Last reviewed: 2026-03-31 (session 9)

---

## Bug Fixes (from code review)

### Quick wins (1–5 min each)
- [x] **Broken 2v2 heading tag** — `<h3></h3>⚔️ 2v2 Team Battle</h3>` → fix opening `<h3>` so text is inside the tag *(1 char fix)*
- [x] **Typo in welcome guide** — `"red joistick"` → `"red joystick"` *(1 char fix)*
- [x] **Remove vestigial CSS comment** — `/* Your existing CSS styles remain the same */` at top of `<style>` *(delete 1 line)*
- [x] **Duplicate `#super-btn-container` CSS** — same rules defined at root level and inside `@media (max-width: 1024px)` *(remove the duplicate block)*

### Medium fixes (~30 min each)
- [x] **Level rewards not persisting** — `milestone.claimed` lives only in memory; re-claimable every page reload. Save/load `claimed` flags to `localStorage` *(add persistence around `levelRewards` array)*
- [x] **`showAllUI()` shows joysticks on desktop** — unconditionally shows joystick elements regardless of device. Add touch/width check matching `startGame()` *(~5 lines)*
- [x] **Bots don't pick up health packs during normal play** — `checkHealthPackCollision(bot)` only called in health-panic branch. Move call so it runs every frame *(move 1 line)*
- [ ] **Naming inconsistency: XP → Medals** — `awardXP()`, `playerXP`, localStorage key `playerXP` still reference old XP name. Rename for clarity *(search-and-replace)*

### Hard fixes (design/logic changes)
- [ ] **Berserk super 2× fire rate broken** — `_baseShootMult` assigned but `shootCooldown` never halved. Implement the fire-rate half for the duration of the super *(add cooldown override in shoot logic)*
- [ ] **Dash supers ignore obstacles** — `rockrush` and `firedash` teleport through walls. Add obstacle collision check along the dash path *(AABB sweep or step-check)*

---

## Remaining Features

### Easy
- [ ] **Settings menu** — Volume slider, toggle joystick visibility, maybe keybinds *(UI panel + a few variables)*
- [ ] **Emotes/taunts** — Press a key to display a short emote above your character *(key handler + draw text bubble)*
- [ ] **Sound effects per character** — Unique shoot/death sounds for each brainrot character *(add sound file refs to `playersData`, play on shoot/death)*

### Medium

- [x] **Star drops** — Post-match loot box with chest open/close animation; random reward (coins or medals); weighted rolls *(chestclose.png → chestopen.png animation, star drop overlay)*
- [x] **Rarity system** — Add rarity tiers to characters (Common, Rare, Epic, Mythic, Legendary). Visual presentation in Bazaar *(data + UI, no new game logic)*
- [ ] **Gadgets** — One-time-use ability per match per character (e.g. dash, shield, heal burst, teleport). Activated by a button/key *(new ability system, UI button, cooldown tracking)*
- [x] **Bounty mode** — Kills give stars; team with most stars when timer ends wins *(new win condition + timer + star tracking HUD)*

### Hard
- [x] **Super ability** — Each character charges a special attack by dealing damage (e.g. Tornader → tornado AoE, Lazerman → piercing beam, Fournakis → fire zone). Bar fills up, press key to unleash *(per-character super definitions, charge meter, new projectile/AoE rendering + collision)*


- [x] **Unique attacks per character** — Some characters get non-laser attacks (e.g. spread shot, boomerang, area blast, homing projectile) *(new projectile types, new rendering + collision logic per character)*
- [x] **Upgrade system** *(depends on rarity)* — Spend coins/medals to upgrade character stats. Based on rarity tier *(depends on rarity system)*

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
- [x] **Poison gas / shrinking zone (Showdown)** — Map slowly shrinks with a damage zone pushing players inward *(zone boundary rendering, periodic damage tick, timer system)*
- [x] **Ball-Goal mode** — Soccer-style: kick a ball into the enemy team's goal to score. First to 2 goals wins *(ball physics, goal zones, score tracking, reset on goal)*
- [x] **Medal system** *(replaces XP)* — Rename XP to Medals (🏅); win = +medals, lose = −medals (like Brawl Stars trophies). Rank based on medal count instead of flat XP *(rework awardXP → awardMedals, update UI/localStorage, add medal loss on defeat)*
- [x] **Respawn system (team modes)** — 15s respawn timer in team modes; respawn near teammate (team battle) or near goalpost (Ball-Goal); no respawn if all teammates dead *(respawnTimer, updateRespawns(), death overlay, skull countdown)*
- [x] **Bug fix: Bazaar unlock** — Fixed Petras/Rocky key mismatch (`Petras:`/`Rocky:` → `petras:`/`rocky:`) that silently blocked unlocking those two characters
- [x] **Bounty mode** — 2-minute 3v3 timer match; kills earn team stars; team with most stars wins; always-respawn (5s); bounty HUD shows countdown + team star counts *(bountyTimerFrames, updateBountyTimer(), drawHUD bounty branch)*
- [x] **Unique attacks per character** — 8 distinct attack types: `standard`, `spread` (3-shot), `triple` (wide 3-fan), `double` (parallel beams), `heavy` (slow ball + AoE), `rapid` (2 quick shots), `homing` (tracks nearest enemy), `boomerang` (returns), `aoehit` (AoE on impact). Bot AI uses same system via `botFireAttack()`. Visual differentiation in `drawLasers()` *(attackType field in playersData, botFireAttack helper, homing/boomerang logic in updateLasers)*