# Game Design Notes

Companion to LORE.md. These are planning notes, not final specs.

---

## Fulcrum Station (starting area)

The current setup already fits the lore, so there's no need to change it. The player starts on the Station, learns to fly, and meets the core features there. See LORE.md → Places for what each area is in the story.

The tutorial can double as the contract signing: Quartermaster Vance hands the player a ship and a Ledger, and gets them fitted with a Lens. The Lens switching on is the moment the HUD appears.

---

## The Ledger (starting debt)

The player starts with the standard Lumenhold contract every pilot has for their first ship. It's normal in this world, which is the point: the modern experience of needing debt to get a start in life. The debt gives an immediate goal, teaches the gameplay loop, and ties the player to the story from minute one. Games that do this well: *Hardspace: Shipbreaker*, *Animal Crossing*.

**Principle:** the debt holds back **Lumenhold privileges**, never the core fun. Players must always have money to spend on their own progress.

- **Automatic share:** a fixed cut (around 15%) of pay from **Lumenhold jobs only** goes to the debt. Money from exploring, trading and other factions is the player's to keep.
- **Optional payments** at any time.
- **Rewards at milestones:** paying off 25 / 50 / 75 / 100% unlocks Lumenhold privileges: better ship licenses, more hangar slots, better jobs, and story chapters.
- **Exploration pays it down:** the Lumenhold buys survey data and discoveries as debt credit at a bonus rate.
- **Ignoring it is allowed:** players who don't pay get worse Lumenhold rates and are listed on debtor notices (flavor only). They lose no gear and no progress. Hearthfleet and Unlit characters may trust them *more* because of it.
- **Paying it off is a story moment:** the player finds a hidden clause. This is the first crack in the Lumenhold's friendly image.
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
- **Basic terms** (the Blink, shards, the Lens) still get a short definition when they first appear, so players never get stuck on a word.

---

## Factions and reputation

- **No locked faction choice.** Players earn reputation with the Hearthfleet, the Meridians and the Unlit separately through quests and choices.
- Reputation unlocks faction quests, cosmetics (banners, colors, clothing), vendors and story.
- Why: Roblox players play with friends. Locking factions splits groups apart and hides content.
- **Possible big choice at the end of a chapter** about the Flame. Restore it? Replace it? Let it go dark? This could be a server-wide event instead of a per-player ending.

## Conflicts as content

Every present-day conflict in LORE.md (the Shard War, the Ledger, the storm rush, Rimeborn, Cinderreach, Umbra salvage, and each faction's internal split) should supply both **repeatable activities** and **quest lines**. Reputation can track a faction *and* which side of its internal split the player leans toward.

## PvP: War Contracts

- The Lumenhold's job board posts contracts for **both sides** of a conflict.
- Taking a contract puts the player on that side **for that battle only**.
- Players are literally mercenaries for the company funding everyone, so the mechanic and the story say the same thing.

---

## Story structure: chapters

- Endless play **and** real endings: the story comes in **chapters or seasons**. Each chapter ends, and the world keeps going.
- **The Blink getting longer** can change across chapters as a server-wide sign of progress.
- Manageable for a solo developer: one chapter at a time.

---

## The Lens (UI) and Truesight

- **The Lens is the UI.** Everything on the HUD (map markers, ship readouts, heat, quest markers, Blink countdown, Ledger balance) is in-world information shown by the Lumenhold eye implant. This gives the UI a lore reason to exist.
- **Low-light mode:** one-color night vision, available to everyone from the start.
- **Truesight:** an upgrade to full color in the dark, earned through the Unlit. Can't see Hollows.
- **Chapter 4 moment:** after the Almanac reveal, the player can switch the Lens to an independent feed, built from Hearthfleet bell-records and Vesper Order measurements. **The Blink countdown on the HUD changes.** The UI itself was lying, which makes the twist something the player sees, not just reads.
- Umbra stays optional rather than a chore: it's where you earn Truesight, and Truesight makes dark places comfortable.

---

## Weapons and ships

- All ships and weapons are standard Lumenhold gear. There's no faction-specific hardware, only cosmetic differences.
- Lore says "**weapons run on flame energy**." The current overheat mechanic fits. Ammo or charge mechanics would fit too, so the lore never needs changing.

---

## MMO structure: a story in a world that repeats

The goal is a long-lived MMO-style game (like Hypixel SkyBlock) with an ongoing story. Those two goals pull against each other: bosses respawn and the world resets, while a story wants things to change. The usual MMO solution splits the game into three layers:

| Layer | What it holds | Changes for |
|---|---|---|
| **The world** | Planets, bosses, the Shard War, the Ion Storm, the economy | Nobody. It stays stable so it can be replayed forever. |
| **Personal story** | Quest chains, the Ledger, Ship's Log mysteries, reputation | One player at a time |
| **World events** | Chapter or season updates, live events, the Blink getting longer | Everyone at once, on a schedule |

**Rules that keep the lore from contradicting the repeating gameplay:**
- **Anything repeatable must not be unique in the lore.** "A Titan", not "the Titan". "Hollowed ships", not one named ghost ship. There are always more.
- **Anything unique happens only once**, in a personal quest or a one-time world event. For example, a story mission that kills one *named* Titan for good.
- **Endless conflicts need a lore reason to be endless.** The Shard War never ends because **Lumenhold keeps it at a stalemate on purpose**. The repeating gameplay *is* the story.
- **The big goal is shared, not personal.** Restoring the Tender (the Ion Storm) and relighting the Damper's anchors in Umbra can be a **server-wide, long-term project** that every player contributes to over seasons. It's a story ending that doesn't stop the game.

---

## Bosses and world events

| Thing | Gameplay | Lore (see LORE.md) |
|---|---|---|
| **Titans** (Cinderreach) | Ship boss with a fleet. Players follow an "Unknown signal" to find one. Drops a **Titan Heart**, which the Forge turns into armor. | Automated Lumenhold harvesters, officially "rogue." There are many. Lumenhold profits whether they survive or not. |
| **The Hollow Fleet** (Umbra) | Ship boss with a fleet | Shard War wrecks taken over by Hollows. The war keeps supplying new ones. |
| **The Ion Storm** | Roaming fog cloud with no surface that can pass over planets. Lightning in the outer layer, a calm center with valuable ore. | A living swarm of **stormdust** that the Old World once harnessed. The fog *is* the creature. |

### Group fights
Titans are hard enough to need a team. That suits an MMO: **Warden Hunts** are open bounty calls from the Cinder Wardens that gather players for a group attack.

### Drops (proposal, beyond Titan Hearts)
| Source | Drop | Possible use |
|---|---|---|
| Titans | **Titan Heart** | Armor at the Forge (current) |
| Titans | **Titan plating** | Hull upgrades |
| Titans | **Cutting beams** | Weapon parts or mining tools |
| Titans | **Survey cores** | Sell to the Meridians, or read them: they carry Lumenhold survey stamps (a Ship's Log clue) |
| Hollow Fleet | **Hollowed shards** (drained and dark) | Low-light or stealth gear, Unlit crafting |
| Hollow Fleet | **Salvage** | General crafting, sold to the Umbra Salvage Guild |
| Ion Storm | **Storm ore** | Current valuable ore |
| Ion Storm | **Stormdust** | Valuable, but it's the living Tender. After Chapter 3, collecting it becomes a moral choice. |

### Titan Hearts: optional choice later
The Forge is enough for now. Later, the Heart can become a **repeatable faction choice**:
- **Forge it:** armor for you. Lumenhold takes its fee.
- **Give it to the Cinder Wardens:** Hearthfleet reputation.
- **Sell it to the Meridians:** Meridian reputation.

That gives players a reason to care about factions every time they kill a boss, with no locked faction choice.

### Ion Storm: gameplay ideas
- **A path players can predict:** it moves slowly and repeats, so players (and the Vesper Order) can chart it. Sell storm forecasts, or put them in the Ship's Log.
- **Shelter during the Blink:** it keeps glowing when the Flame goes dark, and Hollows won't enter it. It becomes a risky-but-safe place to wait out the Blink.
- **Shepherd grains as relics:** rare *made* grains with HELIOS etchings. Old World clues for the Ship's Log.
- *(Optional later)* **Debris in the calm center:** floating ore chunks and wreckage to mine and look at. A good job for the Blender pipeline.
- **Everyone wants it:** Lumenhold sells "storm insurance", and the factions race for the ore.

---

## Content maturity

- Aim for the **lowest Roblox content maturity rating that fits**, so the most players can find the game.
- Themes like debt, corruption, war profiteering and refugees don't raise the rating. Graphic violence and gore do.
- Fill out Roblox's maturity questionnaire honestly once the content is real.
