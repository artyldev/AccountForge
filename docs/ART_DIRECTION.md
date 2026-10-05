# Art Direction

Working notes for building assets. Apply these when production starts.

---

## Style: semi-realistic (stylized realism)

- **Shapes:** readable and slightly simplified, like the current Quaternius ships.
- **Surfaces:** realistic **PBR** materials (textures that react to light like real metal, paint, rock and so on), so assets match Roblox's built-in terrain.
- **Not** fully flat-colored, and **not** photorealistic.

### Vocabulary
- **Low-poly / high-poly:** how much shape detail a model has (its polygon count).
- **Flat-shaded / flat colors:** one plain color per surface, no texture.
- **Stylized vs. realistic:** the overall look.
- **PBR:** physically based rendering. In Roblox this means a **SurfaceAppearance** with four maps: Color, Normal, Roughness, Metalness.

---

## Surface rules: wear and tear

Assets should look **used**. Plain, uniform surfaces are what look cheap.

- **Edge wear:** paint chipped off exposed edges and corners, showing bare metal underneath.
- **Scratches:** concentrated where things get touched or bumped: hatches, handles, landing gear, gun grips.
- **Grime:** dirt collected in crevices, seams and panel gaps (baked ambient occlusion helps here).
- **Panel lines:** surface detail carried by the normal map, not by extra polygons.
- **Roughness variation:** never one uniform roughness value. Worn spots are shinier and dirty spots duller.
- **Color variation:** subtle patchiness and fading. Never a perfectly even color.
- **Markings:** decals for Lumenhold logos, hull numbers, warning stripes and faction banners.
- **Bevels:** no razor-sharp 90° edges. Slight bevels catch light.

### Common mistakes
- Mixing flat-colored assets with PBR assets in the same scene.
- Wear applied evenly everywhere. Real wear follows use.
- Procedural shaders left unbaked in Blender. **Roblox can only use baked image maps.**

---

## Lumenhold look (all standard ships and weapons)

All standard gear is Lumenhold-made, so it shares one visual language.

- **Tentative palette:** off-white hull `#D9D4C7`, gunmetal `#3A3F47`, Lumenhold amber `#E0A43A`, with bare-metal chips showing through worn paint.
- Industrial, practical, slightly old-fashioned: rivets, heavy hatches, stenciled labels.
- **Faction cosmetics** sit on top: banners, colors, small decals. The hull itself stays standard.

---

## Old World look (Ion Storm, relics)

This must look clearly different from Lumenhold gear, so players can tell old from new at a glance.

- **The Ion Storm:** fog with a faint shimmer. Up close it should look made of tiny glinting particles, not just cloud. Its own cold white-blue glow (distinct from Lumenhold amber), which stays visible during the Blink.
- **Relics** (dead motes, the gold disc, coins): smooth, cast-looking shapes. Weathered over centuries: patina, pitting, faded markings, not chipped paint. Faint "HELIOS" etchings.
- **Optional debris in the calm center:** ore chunks fused with glinting mote residue.

---

## Boss ship looks (built from existing ship models)

- **Titans:** Lumenhold design language at a much bigger scale. Make it by **kitbashing** (combining parts from several existing ship models) and adding heavy armor plates, extra weapons and an exposed glowing Heart, and mining equipment (they're harvesters). Scrubbed or missing markings, since they're unregistered. Small differences between individual Titans help sell "there are many."
- **The Hollow Fleet:** standard Lumenhold hulls, battle-damaged, with all lights out, cold dark shard cores, and frost or dark residue. The same models with a different material pass.

---

## Where to get ship models

Always check the license. A monetized Roblox game needs a license that **allows commercial use** and **allows modification**.

- **Quaternius:** CC0 (free for any use). You're already using this.
- **Kenney:** CC0. More low-poly, but useful for parts.
- **Sketchfab:** filter for downloadable models. CC0 and CC-BY are fine (CC-BY needs a credit). Avoid NonCommercial (NC) and NoDerivatives (ND).
- **itch.io asset packs:** free and paid. Licenses vary, so read each one.
- **Paid stores** (CGTrader, TurboSquid, Synty): higher quality, with commercial licenses. Synty is low-poly, which may not match.
- **AI mesh generators** (Roblox generate_mesh, Hunyuan3D, Meshy, Tripo): uneven quality. Best used for parts to kitbash, not whole hero ships.
- **Roblox Creator Store:** check for hidden scripts before using anything.

**The cheapest way to get unique bosses:** kitbash the ships you already have in Blender, scale them up, add armor, and retexture with the wear-and-tear rules. That's a good second job for the pipeline, after the Lumenhold ship remaster.

---

## Lighting presets to test assets against

1. **Day:** normal Elder Flame light.
2. **The Blink:** near-total dark. Check that glowing parts and silhouettes still read.
3. **Dusklens:** single-color night vision view.
4. **Region moods:** Umbra (dark), Rimefall (cold and blue), Cinderreach (hot and orange).

---

## Technical limits (Roblox)

Check these against current Roblox documentation before relying on them.

- At most **21,000 triangles per MeshPart**. Aim much lower for props.
- Texture maps up to 4096px. Use **1024px** by default and 512px for small props.
- Rough texture density guide: 256px per 2×2×2 studs.
- Normal maps in **OpenGL format** (Y+), which is Blender's default.

---

## Blender pipeline

The plan is a scripted, headless Blender pipeline in this repo. Each asset is a Python script, and the pipeline renders previews for review.

**First test asset:** take one Quaternius ship and produce a **Lumenhold-issued** semi-realistic version:
- PBR materials
- edge wear, scratches and grime
- panel lines
- Lumenhold markings
- baked to the four SurfaceAppearance maps
- exported as FBX for Roblox

**Review loop:** render from four angles, plus one "baked-only" render showing exactly what Roblox will display. Critique against this document, fix, and repeat (up to 4 rounds).

The full handoff prompt for setting this up is in the planning conversation. It should be updated to use the Quaternius ship as the baseline instead of the earlier test assets.
