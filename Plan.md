# The Mines of Mukduk — Design Plan

> s&box project planning doc. Fill in, delete what you don't need.

- **Working title:** The Mines of Mukduk
- **Genre:** Action RPG (ARPG) — dungeon-escape / dungeon crawler
- **Elevator pitch:** Trapped at the bottom of the Mines of Mukduk with nothing, claw your way deeper, scavenge and forge your power, and fight your way out.
- **Player count:** Singleplayer (co-op as a stretch goal)
- **Run length:** A full run targets **several hours**, with **save & resume** so players can stop and continue later.
- **Status:** Concept

---

## 1. Vision & Pillars
What this game *is* and the core ideas everything serves.

- **Pillar 1 — Earned power.** You start with *nothing*. Every weapon, every upgrade is scavenged or forged, so progression always feels earned. The early game is deliberately weak and improvised (a rock, a broken pickaxe).
- **Pillar 2 — Descend to escape.** The way out isn't up — it's deeper. Going down is the only way forward, which creates dread and constant forward pull instead of backtracking.
- **Pillar 3 — Tension through scarcity.** Light, stamina, and resources are limited. Darkness is dangerous; greed is punished; staying too long gets you killed.
- **The fantasy / why it's fun:** From naked and terrified to a forged-out, geared-up survivor — every item you find is a moment of relief because you genuinely struggled without it.
- **References / inspirations:** Diablo, Hades, Dark Souls (loot recovery), Dead Cells, Spelunky (descent).

---

## 2. Gameplay
### Core loop
Explore a mine tier → fight & mine for loot/resources → forge/upgrade gear → descend deeper → survive escalating threat → reach the exit (deeper down).

### Combat — **real-time action** (not turn-based)
Decision: real-time action combat. It's the "A" in ARPG, plays to s&box's (Source 2) real-time strengths, and makes "start weak, grow strong" something you *feel*.

- **Camera:** Isometric / top-down ARPG view — simpler controls, collision, and readability for a small team. _(Third-person over-shoulder is the alternative if you want more immersion + animation work.)_
- **Core verbs:** light attack, heavy attack, dodge/roll, block, one skill slot early that expands with gear.
- **Stamina-gated:** attacks and dodges cost stamina — no spamming. Ties into weight/loadout choices.
- **Telegraphed enemies:** wind-up animations so dodging is skill, not luck.
- **Weapon identity:**
  - Pickaxe — slow, heavy, **doubles as a mining tool**
  - Daggers — fast, weak, combo-focused
  - Thrown rocks / ranged — situational
- **Status & elemental damage:** fire / poison / shock for build variety.

### Mechanics
- **Movement:** real-time, dodge-roll, stamina-limited; armor weight affects speed.
- **Scavenge-based gear:** loot from kills, chests, mined veins, corpses. ARPG rarity tiers (common → rare → unique) with affixes.
- **Mining as a verb:** dig through walls for shortcuts, hidden caches, or to collapse tunnels on enemies. Raw ore feeds the forge.
- **Crafting / forge stations:** turn ore + scrap into upgraded gear; forges double as semi-safe checkpoints.
- **Light & resource scarcity:** torches / lantern oil as consumables — darkness = danger.
- **Escalating threat:** the longer you linger on a tier, the worse it gets (stronger spawns / rising hazard) — pushes the escape.
- **Win condition:** reach the final exit at the bottom of the mine.
- **Lose condition:** death — see Run Model below.

### Controls (draft)
| Input | Action |
|-------|--------|
| WASD / move | Movement |
| LMB | Light attack |
| RMB | Heavy attack |
| Space | Dodge / roll |
| Shift | Block / guard |
| E | Interact / mine / loot |
| Q | Use skill |
| Tab / I | Inventory |

### Difficulty & pacing
- **A full run targets several hours.** Pace progression so the descent fills that arc: weak/improvised → forged-up → confronting the bottom.
- Players can **save and resume mid-run** — see Run Model (§8) and Save System (§6).
- Ramp from genuinely weak/improvised to powered-up over a descent.
- Risk/reward side paths: sealed vaults, cursed loot, "greed" rooms with tough guards.

---

## 3. Story & World
- **Setting:** The Mines of Mukduk — a deep, abandoned (cursed?) mining complex. Dark, claustrophobic, escalating dread the deeper you go.
- **Premise:** You wake at the bottom with nothing. The only way out is *down and through*. Why are you here? What's at the bottom?
- **Main character / player role:** A prisoner / lost miner / scavenger _(TBD)_.
- **Key NPCs / factions:** _(TBD — consider a rival escapee you can trade with, race, or betray.)_
- **Narrative delivery:** Primarily environmental (corpses, carvings, abandoned camps) + sparse found notes.
- **Story beats / arc:**
  1. Wake with nothing — survive the first tier, find an improvised weapon.
  2. Discover the first forge — power begins; learn the mine is more than it seems.
  3. Mid-depth revelation — why you're trapped / what's hunting you.
  4. The bottom — confrontation + the route to escape.

---

## 4. Levels & Content
- **Structure:** **NOT open world.** Descending depth tiers (Mine Level 1 → 2 → 3 → deeper), connected by gated passages — preserves escape tension without open-world cost.
- **Level generation:** **Procedurally generated** via **room-template assembly** — the dungeon is built at runtime by stitching together a hand-authored library of room/corridor pieces using a per-tier **seed**. This gives endless variety while keeping spaces readable, balanced, and bug-free (no unreachable rooms, no boss in a corridor). Special pieces (boss arenas, vaults, forge rooms, the tier exit) are tagged so the generator places exactly one where needed. _(This is procedural — just procedural-from-pieces, not procedural-from-noise, which tends to feel samey and produce layout bugs over a multi-hour run.)_
  - **Generation rules to define:** piece tag types (combat / loot / forge / boss / exit / connector), min/max rooms per tier, guaranteed pieces per tier, difficulty weighting by depth, dead-end vs. loop ratio.
  - **Determinism is mandatory:** same seed → same layout, so the save system can regenerate a tier and re-apply the world-state diff (mined walls, looted chests, kills) on resume.
- **Gating:** find keys / levers / relics to open the path deeper; paces progression.
- **Planned tiers (v1):**
  - Tier 1 — Upper shafts (tutorial-feel, improvised gear)
  - Tier 2 — Flooded / collapsed works (first forge, hazards)
  - Tier 3 — The deep dark (escalated threat, mini-boss)
  - Tier 4 — The bottom (final encounter + exit)
- **Content scope (v1):** 3–4 tiers + 1 boss as the vertical slice target.

---

## 5. Art & Audio
- **Visual style:** Dark, grimy mine; strong light/shadow contrast to sell the torch/scarcity mechanic. _(Stylized over realistic = cheaper, ages better.)_
- **Camera:** Isometric / top-down.
- **Key assets needed:** Player + improvised/forged weapons, 2–3 enemy types per tier, mine tilesets/rooms, forge station, torch/lighting, chests/ore veins.
- **Music & SFX direction:** Sparse, tense ambience; escalating tension audio when the "stay too long" threat ramps.
- **UI / HUD:** Health, stamina, light/oil meter, minimal inventory. Build in Razor panels.

---

## 6. Technical (s&box specific)
- **Game type:** Component-based GameObject scene.
- **Networking:** Singleplayer first; architect the player controller and game state to *allow* co-op later, but don't build it yet.

### Save / resume system (critical — drives architecture)
A run is several hours and must be resumable, so the save system is a first-class system, not an afterthought.
- **Seed-based deterministic procgen.** Save a **seed per tier**, not the whole geometry. Regenerate the layout from the seed on load.
- **World-state delta.** On top of the regenerated layout, persist a **diff of changes**: mined-out walls, opened chests, looted items, killed enemies, dropped/corpse loot, gates opened.
- **Player save blob:** position, current tier, inventory/equipment, stats, stamina, consumables (oil), forge/upgrade state.
- **Save trigger policy:** checkpoint saves at **forges** + a **suspend-on-quit** save so players can stop anytime. (Death still has consequences — see Run Model.)
- **Single save slot per character** (resume = load that slot). Decide whether quitting mid-tier is fully safe or only forges are "hard" checkpoints.
- **Core systems to build:**
  - [ ] Player controller (real-time, stamina, dodge)
  - [ ] Isometric camera
  - [ ] Combat system (attacks, hit detection, telegraphs)
  - [ ] Loot / inventory + rarity/affix system
  - [ ] Mining + destructible walls
  - [ ] Forge / crafting + upgrade
  - [ ] Lighting / torch-oil resource
  - [ ] Procedural tier generator (seed-based room-template assembly)
  - [ ] Room-piece library (authored prefabs, tagged by type)
  - [ ] Enemy AI + spawning / escalation
  - [ ] Game state / run manager (death, descent)
  - [ ] **Save / resume system (seed + world-state delta + player blob)**
  - [ ] UI / HUD (Razor)
- **Assets / addons:** s&box asset library for prototyping; custom models later.
- **Performance targets:** _(TBD — set once a tier is greyboxed.)_

---

## 7. Scope & Milestones
| Milestone | Goal | Done? |
|-----------|------|-------|
| Prototype | One greybox tier: move, attack, dodge, loot one item, descend | ☐ |
| Vertical slice | Tier 1–2 polished, forge working, one mini-boss | ☐ |
| Content complete | All v1 tiers + final boss + escape | ☐ |
| Release | Published to s&box | ☐ |

### MVP — smallest playable thing
Spawn naked in one room → fight one enemy → pick up first weapon → mine a wall → reach a stairwell down. If that loop *feels* good, the game works.

### Stretch goals
- Co-op
- Rival escapee NPC (trade / betray / race)
- Sanity/fear meter in deep sections
- Meta-progression hub between runs

---

## 8. Risks & Open Questions
- **Run model — RESOLVED by the several-hour/saveable goal → Souls-like recovery (persistent).** A multi-hour run makes classic short-loop **permadeath roguelite a poor fit** (losing hours to one death feels punishing) and requires full mid-run persistence anyway. So: **persistent character, save & resume, death respawns you at the last forge with your loot left on your corpse to retrieve.** Keeps tension without wiping hours of progress. _(If you ever want more replayability, layer optional meta-unlocks on top — but the spine is persistent.)_
- **Risk:** Procedural generation that still feels good is hard — use **room-template assembly** (stitch authored pieces by seed), not pure noise. Start with a small piece library and a simple stitch algorithm, then expand the library for variety.
- **Risk:** Scope. Loot/affix + crafting + procgen + AI is a lot for a small team — protect the MVP loop first.
- **Unknown:** Who is the player, and what's at the bottom of the mine? (Story TBD.)
- **Decision:** Isometric vs third-person camera — currently isometric for simplicity.

---

## 9. Notes & Scratch
- "Mukduk" — lean into the name? Is Mukduk a place, a god, a monster at the bottom?
- Death-drops-loot mechanic pairs perfectly with the Souls-like run model — recovering your own corpse becomes a tense mini-objective.
