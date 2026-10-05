# Blender Pipeline: Getting High-Quality Assets with Claude

How to get good-looking models out of Blender with Claude's help, and avoid the flat, plastic results from earlier attempts. Art rules (style, wear and tear, palette, Roblox limits) are in ART_DIRECTION.md; this doc is the *method*.

---

## Why earlier results looked flat

1. **Claude was building without seeing.** It stacked basic shapes and gave each a single color, with no way to look at the result.
2. **Single-color materials.** Real surfaces have variation, wear, dirt and roughness changes. One flat color per part always looks cheap.
3. **No bevels.** Razor-sharp 90° edges don't catch light, and that's what reads as "plastic."
4. **Procedural materials that never reached Roblox.** **Roblox can't read Blender's shader nodes.** A material that looks great in Blender shows up as one flat color in Roblox unless it's *baked* into image maps.

---

## The strategy

### 1. Split the work by what each tool is good at
| Asset type | Who makes it | How |
|---|---|---|
| Buildings, stations, modular pieces, props, layout | **Claude** | Python-scripted geometry in Blender. Claude is strong at precise, rule-based building. |
| Ships | **Existing models + Claude** | Start from the Quaternius ships. Claude adds materials, wear, markings, and kitbashes parts for bosses. |
| Organic shapes (creatures, characters) | **AI mesh generators or existing assets** | Claude is weak at sculpting organic shapes with code. Use generated or downloaded meshes, then let Claude handle cleanup, UVs, baking and export. |
| Textures | **Real PBR texture sets** | Poly Haven or ambientCG (both CC0, free for any use), or procedural materials that get baked |

### 2. Let Claude see its work
The single biggest improvement. Every asset goes through a loop:

**build → render from several angles → compare to the reference and the rubric → list what's wrong → fix → render again.**

Give Claude a reference image whenever you can. Without renders it's guessing.

### 3. Write the style down once
The style rules in ART_DIRECTION.md (semi-realistic, wear and tear, palette, the three visual eras) are what every asset is checked against. A consistent style is what makes assets look intentional instead of mismatched.

---

## Two ways to drive Blender

| | **A. Scripted pipeline in this repo** (recommended) | **B. Blender MCP on your computer** |
|---|---|---|
| How it works | Claude writes a Python script per asset and runs Blender headless (no window): `blender -b -P build.py` | Claude controls a live Blender window through an MCP connection |
| How Claude sees results | Rendered preview images | Viewport screenshots |
| Strengths | Repeatable, version-controlled, adjustable with one setting ("20% more rust"). Works in cloud sessions. | Interactive. You can tweak by hand in between. |
| Weaknesses | No live window (you can still open the saved .blend file) | One-off changes, hard to repeat. Runs any Python code. |

**Blender MCP safety** (`ahujasid/blender-mcp`): save your work first, keep it on your own computer only (its connection has no password), turn on safe mode (`BLENDER_MCP_SAFE_MODE=1`), check its telemetry setting, and install with the exact command from its README.

---

## The steps every asset goes through

1. **Blockout:** rough shapes at correct Roblox scale, with a human-sized reference figure in renders (not exported).
2. **Detail:** a Bevel modifier and Weighted Normal on all hard-surface parts. Booleans and inserts for secondary shapes. Break up silhouettes. No unedited primitives.
3. **UVs:** unwrap so textures map without stretching, at a consistent texture density (guide: about 256px per 2×2×2 studs).
4. **Materials:** never a single flat color. Either a real PBR texture set, or a procedural material with at least:
   - base color variation (noise),
   - edge wear (curvature or ambient occlusion),
   - grime in crevices,
   - roughness variation.
5. **Bake:** Roblox can't read shader nodes. Bake to **four maps** for a SurfaceAppearance: **Color, Normal (OpenGL format), Roughness, Metalness**. 1024px by default, 512px for small props. If there's a detailed high-poly version, bake its detail onto the low-poly normal map, so you get the detail without the triangle cost.
6. **Validate and export:**
   - at most 21,000 triangles per mesh (aim much lower),
   - transforms applied, origin at the base,
   - clean names, no unused materials.

   Fail loudly if anything's wrong. Export FBX plus the four PNGs.
7. **Review:** render front, three-quarter, top and close-up under a fixed lighting setup, **plus a "baked-only" render** showing exactly what Roblox will display. Score it against the rubric below, fix, re-render. At most 4 rounds.

### Getting it into Roblox
Import the FBX with Studio's 3D Importer, add a **SurfaceAppearance**, and assign the four maps. Then check it under the game's lighting presets: day, the Blink, Lens low-light mode, and the region moods (ART_DIRECTION.md).

---

## Quality rubric

Score each 1–5. Pass only if **nothing is below 3 and the average is at least 4**. If an asset can't pass in 4 rounds, stop and report what's holding it back. Don't inflate scores.

1. **Silhouette and proportion** read clearly at gameplay distance.
2. **Surface detail:** wear, variation, no flat or plastic-looking areas.
3. **Edges catch light:** bevels visible in renders.
4. **Matches the style** in ART_DIRECTION.md: the right era, palette and level of wear.
5. **The baked-only render matches the full render**, with only a small loss.
6. **Technical:** triangle count, texture size, scale and naming are all correct.

---

## Handoff prompt

Paste this into a new Claude Code session in this repo to set up the pipeline and make the first asset. It points to the docs instead of repeating them, so it stays up to date.

````markdown
# Task: Build the Blender → Roblox asset pipeline and remaster one ship

Read these first: docs/BLENDER_PIPELINE.md (the method) and docs/ART_DIRECTION.md (the style,
wear-and-tear rules, Lumenhold look, palette, Roblox limits). Follow them exactly.

## Setup
- Download the latest Blender LTS for Linux x64 from download.blender.org (verify the checksum).
  Add `blender/setup.sh` that installs it idempotently into a local tools folder (gitignored).
- Run headless: `blender -b -P <script> -- <args>`. Render previews with Cycles on CPU
  (~64 samples + denoise, 1024×1024).
- Textures and HDRIs: Poly Haven or ambientCG, CC0 only. Log each one with its URL in
  `blender/CREDITS.md`. Cache downloads and gitignore the cache.

## Repo layout
blender/
  setup.sh, README.md, CREDITS.md
  lib/  scene.py (scale, lighting rig, HDRI) · geo.py (bevels, weighted normals, cleanup)
        materials.py (PBR loader + wear/grime/variation presets) · uv.py · bake.py (4 maps)
        export.py (validation + FBX) · review.py (4 angles + baked-only render + contact sheet)
  assets/<name>/build.py   one parametric script per asset
  out/<name>/              .blend, .fbx, 4 PNG maps, renders/, REVIEW.md

## First asset: a Lumenhold-issued ship
I'll provide one Quaternius ship model (from the "Ultimate Spaceships" pack) in `blender/source/`.
Remaster it into a semi-realistic Lumenhold standard-issue ship:
- PBR materials in the Lumenhold palette (ART_DIRECTION.md), not flat colors
- bevels where edges are too sharp, panel lines in the normal map
- edge wear and scratches where things get touched, grime in seams, roughness variation
- Lumenhold markings: logo, hull number, warning stripes (decals or baked)
- baked to the 4 SurfaceAppearance maps, validated, exported as FBX

Follow the review loop and rubric in BLENDER_PIPELINE.md. Write scores and the contact sheet into
out/<name>/REVIEW.md. Max 4 rounds; say plainly which rubric items are weakest.

## Then
- Turn the pipeline into a project skill at `.claude/skills/roblox-asset/SKILL.md` (description:
  "Build or remaster a game-ready Roblox asset in Blender. Use when asked to model, texture,
  remaster or export a ship, prop, structure or environment piece.") pointing to blender/lib
  and the docs.
- Commit in logical steps and push to the session's working branch. Show me the contact sheet.
````

### Good next assets after the first ship
- **A Hollowed version** of the same ship: lights out, battle damage, frost or dark residue (the Hollow Fleet).
- **A Titan:** several ships kitbashed together at a larger scale, with armor plates, mining gear and a glowing Heart.
- **A light-sail barge wreck:** Firstlight timber and brass with torn sails (static set dressing).
- **The Titan cut lines:** straight glowing cuts in Cinderreach rock (needed for the end of Chapter 1).
