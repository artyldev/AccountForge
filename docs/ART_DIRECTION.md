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
- **Markings:** decals for Consortium logos, hull numbers, warning stripes and faction banners.
- **Bevels:** no razor-sharp 90° edges. Slight bevels catch light.

### Common mistakes
- Mixing flat-colored assets with PBR assets in the same scene.
- Wear applied evenly everywhere. Real wear follows use.
- Procedural shaders left unbaked in Blender. **Roblox can only use baked image maps.**

---

## Consortium look (all standard ships and weapons)

All standard gear is Consortium-made, so it shares one visual language.

- **Tentative palette:** off-white hull `#D9D4C7`, gunmetal `#3A3F47`, Consortium amber `#E0A43A`, with bare-metal chips showing through worn paint.
- Industrial, practical, slightly old-fashioned: rivets, heavy hatches, stenciled labels.
- **Faction cosmetics** sit on top: banners, colors, small decals. The hull itself stays standard.

---

## Old World look (Titans, relics)

This must look clearly different from Consortium gear, so players can tell old from new at a glance.

- Smoother, more unified shapes. Fewer visible rivets and bolted-on parts. It looks grown or cast rather than assembled.
- Weathered over centuries: heavy patina, dust, pitting, faded markings. Not chipped paint.
- Its own accent color, distinct from Consortium amber (for example a cold white-blue glow from the Heart).
- Faint "HELIOS" markings on hulls, half worn away.

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

**First test asset:** take one Quaternius ship and produce a **Consortium-issued** semi-realistic version:
- PBR materials
- edge wear, scratches and grime
- panel lines
- Consortium markings
- baked to the four SurfaceAppearance maps
- exported as FBX for Roblox

**Review loop:** render from four angles, plus one "baked-only" render showing exactly what Roblox will display. Critique against this document, fix, and repeat (up to 4 rounds).

The full handoff prompt for setting this up is in the planning conversation. It should be updated to use the Quaternius ship as the baseline instead of the earlier test assets.
