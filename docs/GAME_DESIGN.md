# Game Design Notes

Companion to LORE.md. These are planning notes, not final specs.

---

## The Station (starting area)

The current setup already fits the lore, so there's no need to change it. The player starts on the Station, learns to fly, and meets the core features there.

| Feature | Lore role |
|---|---|
| Mini markets | Consortium company stores with fixed prices |
| Auction house | Consortium-run; takes a cut of every sale |
| Bazaar | Independent traders who pay the Consortium rent |
| Shipyard | Builds every ship in the system |
| Social area | Neutral ground where every side of the war meets |

The tutorial can double as the contract signing: the player is handed a ship, a Dusklens and a Ledger in the first scene.

---

## The Ledger (starting debt)

The player starts with the standard Consortium contract every pilot has for their first ship. It's normal in this world, which is the point: the modern experience of needing debt to get a start in life. The debt gives an immediate goal, teaches the gameplay loop, and ties the player to the story from minute one. Games that do this well: *Hardspace: Shipbreaker*, *Animal Crossing*.

**Principle:** the debt holds back **Consortium privileges**, never the core fun. Players must always have money to spend on their own progress.

- **Automatic share:** a fixed cut (around 15%) of pay from **Consortium jobs only** goes to the debt. Money from exploring, trading and other factions is the player's to keep.
- **Optional payments** at any time.
- **Rewards at milestones:** paying off 25 / 50 / 75 / 100% unlocks Consortium privileges: better ship licenses, more hangar slots, better jobs, and story chapters.
- **Exploration pays it down:** the Consortium buys survey data and discoveries as debt credit at a bonus rate.
- **Ignoring it is allowed:** players who don't pay get worse Consortium rates and are listed on debtor notices (flavor only). They lose no gear and no progress. Hearthfleet and Unlit characters may trust them *more* because of it.
- **Paying it off is a story moment:** the player finds a hidden clause. This is the first crack in the Consortium's friendly image.
- **First payment within about 10–15 minutes** of starting, so the goal feels reachable.

**Never:**
- deadlines or timers
- interest that grows while the player is offline
- permanent repossession of ships or gear
- paying the debt with Robux (that turns a story about predatory debt into actual predatory monetization)

---

## The Ship's Log (discovering the lore)

This replaces a plain encyclopedia. Lore is a **mystery players investigate**, and the log tracks what they've figured out. References: the ship's log in *Outer Wilds*, and *Return of the Obra Dinn*.

- Each **mystery** (see LORE.md → Mysteries) is an entry with clue slots.
- **Clues** come from exploring: wrecks, ruins, recordings, NPC conversations, Old World relics.
- Entries show their state:
  - **Unknown:** `???` plus a hint about where to look.
  - **Rumored:** conflicting accounts, each credited to who said it ("The Hearthfleet say…", "The Flame Almanac states…"). Players can see the truth is disputed.
  - **Solved:** once the key clues are found, the player gets a **Revelation**: the answer, a short story moment and a reward.
- **Permanent mysteries** (like HELIOS) are marked as **Lost**, so players know nobody has the answer, not just them.
- **Basic terms** (the Blink, shards, Dusklens) still get a short definition when they first appear, so players never get stuck on a word.

---

## Factions and reputation

- **No locked faction choice.** Players earn reputation with the Hearthfleet, the Meridians and the Unlit separately through quests and choices.
- Reputation unlocks faction quests, cosmetics (banners, colors, clothing), vendors and story.
- Why: Roblox players play with friends. Locking factions splits groups apart and hides content.
- **Possible big choice at the end of a chapter** about the Flame. Restore it? Replace it? Let it go dark? This could be a server-wide event instead of a per-player ending.

## PvP: War Contracts

- The Consortium's job board posts contracts for **both sides** of a conflict.
- Taking a contract puts the player on that side **for that battle only**.
- Players are literally mercenaries for the company funding everyone, so the mechanic and the story say the same thing.

---

## Story structure: chapters

- Endless play **and** real endings: the story comes in **chapters or seasons**. Each chapter ends, and the world keeps going.
- **The Blink getting longer** can change across chapters as a server-wide sign of progress.
- Manageable for a solo developer: one chapter at a time.

---

## Vision gear

- **Dusklens:** everyone gets it from the start. Shows one color in the dark.
- **Truesight:** an upgrade to full-color vision, earned through the Unlit. Can't see Hollows (see LORE.md).
- This makes Umbra optional rather than a chore: it's where you earn the upgrade, and the upgrade makes dark places comfortable.

---

## Weapons and ships

- All ships and weapons are standard Consortium gear. There's no faction-specific hardware, only cosmetic differences.
- Lore says "**weapons run on flame energy**." The current overheat mechanic fits. Ammo or charge mechanics would fit too, so the lore never needs changing.

---

## Bosses and world events

| Thing | Gameplay | Lore |
|---|---|---|
| **The Titan** (Cinderreach) | Large boss ship. Players follow an "Unknown signal" to find it. Drops a Titan Heart. | An Old World vessel drawn to the burning shard's heat. It repairs itself, which is why it respawns, and rebuilds its Heart each time. |
| **Umbra boss** | TBD | Should tie to the Maw or Hollows (for example, something Truesight can't see) |
| **The Ion Storm** | Roaming, planet-sized storm. Lightning in the outer cloud, a safe eye with valuable ore. | A leftover of the Great Flare. Lightning has fused rare ore in the eye over centuries. |

Open: what are Titan Hearts used for in-game? The lore makes them the most sought-after item in the system, so their use should feel important.

---

## Content maturity

- Aim for the **lowest Roblox content maturity rating that fits**, so the most players can find the game.
- Themes like debt, corruption, war profiteering and refugees don't raise the rating. Graphic violence and gore do.
- Fill out Roblox's maturity questionnaire honestly once the content is real.
