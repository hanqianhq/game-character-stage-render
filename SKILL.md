---
name: wow-transmog-render
description: 将魔兽世界角色截图、幻化参考图或角色渲染图转译为 3:4 暗黑舞台写实展示图。保留身份与装备设计，同时重建布料、皮革、金属、骨骼等材质的体积、结构与光照；亡灵默认使用弯腰驼背姿态。
---

# Game Character Stage Render

Create a premium full-body 3:4 character showcase in an abstract dark studio void. Preserve identity and equipment while rebuilding volume, materials and illumination. The house presentation is visually centered, with roughly balanced space on all four sides, no apparent light source anywhere in the frame, and no ground reflections.

## Choose the character finish

- **Anime / 二次元: default to semi-realistic 3D.** Retain recognizable stylized facial proportions, eye shape, hairstyle, expression, body silhouette and costume. Add believable volume, soft skin shading, strand hair and physical materials. Do not convert the character into a real human, cosplayer, wax figure or plastic collectible. Avoid aggressive pores, aging and facial restructuring that erase the original appeal. The target is anime identity with refined semi-realistic materials and illumination, not flat cel shading or painted concept art.
- **Realistic game characters and armor: default to realistic AAA / Unreal Engine 5 quality.** Rebuild layered geometry and physical materials without redesigning the character.
- Explicit finish requests override defaults. Unreal Engine 5 describes render quality; it does not require photorealistic human anatomy for every subject. Anime identity itself is not a failure mode.

## Composition and framing

- Use exact 3:4 portrait unless requested otherwise. Show the complete requested silhouette, including hair, ears, cape, tail, hands, feet and included equipment. Include weapons when requested or essential to identity; otherwise remove them cleanly.
- **Default subject height is about 64%**, calibrated to the approved Ellen image below. About 62–68% is useful guidance, not a mechanical pass/fail rule. Use roughly 19% top space and 16–17% bottom space: the slightly lower placement and ample upper void are intentional. An approved proportion reference or explicit size instruction takes priority. Do not enlarge the default back to the former 72%, or impose equal upper/lower margins on an accepted composition.
- **Center visually**, balancing the main body with its complete silhouette. Keep the main body near the horizontal center, with grounded weight and relaxed asymmetry; weapon, tail, cape and hair should balance the surrounding negative space. Judge the whole image, not the face or a single appendage. All four sides need breathing room, but neither four equal gaps nor identical top/bottom gaps are required. Preserve the approved reference's margin relationships rather than forcing mathematical symmetry.
- Use the complete silhouette bounding box as a diagnostic. Thin extended weapons, tails or stray hair must not drag the main body visibly off-center. Allow small optical placement adjustments while keeping every appendage fully visible. Do not deliberately place the character off-axis by default.
- Preserve anatomy with camera distance and a moderate long lens, around 70mm. Use near-front presentation with a mild three-quarter turn. Avoid cropping, wide-angle stretching and dramatic low-angle foreshortening.
- A normal screenshot/cutout supplies identity and gear; its framing is non-binding. A user-approved composition/proportion reference supplies framing as well and takes priority over numerical presets.

### Numerical guidance, not a pixel lock

For canvas `W × H` and silhouette bounds `(x_left, y_top, x_right, y_bottom)`, estimate `h = y_bottom - y_top`, `q = h / H`, and margins `T = y_top`, `B = H - y_bottom`, `L = x_left`, `R = W - x_right`. Include requested gear; exclude smoke, particles, glow and contact shadows.

For an unreferenced default, prompt `q ≈ 0.64–0.65`, `y_top ≈ 0.19H`, `y_bottom ≈ 0.835H`, then judge side gaps and visual balance. On 1086×1448 this means about 930–935px subject height, 275px above and 240px below. For a similarly broad silhouette, side gaps near 15–17% of width are useful; narrower characters naturally leave wider side gaps. Do not stretch the pose or invent appendages to force the example's width. These are approximate guides. A pleasing approved image should not trigger regeneration over small numerical differences or a one-percent margin tolerance.

For “increase 5%,” use `h_target = h_source * 1.05`, scaling width equally, not adding five percentage points. Preserve design, pose and approved framing; adjust placement only enough to maintain visual balance. Compare normalized sizes if resolution changes. Fix a placement error by translation, not resizing.

### Primary composition standard: Ellen

Inspect [the approved Ellen render](references/ellen-composition-standard.png) when creating a new showcase with default house framing. The user explicitly selected this image as the standard for visual weight, subject size and all four margins. It supersedes the earlier Jane Doe example as the default. Assign it **composition and stage-presentation roles only** when rendering another character; preserve the new identity reference's own face, pose, costume, gear and palette.

On its 1086×1448 canvas, visually estimated complete silhouette bounds are `x≈177–920`, `y≈276–1212`: height about 64.6%, width about 68.4%; top gap about 276px (19.1% H), bottom about 236px (16.3% H), left about 177px (16.3% W), right about 166px (15.3% W). These approximate measurements describe an accepted image, not an exact pixel mask to impose on every anatomy.

The main body reads near horizontal center, with a natural weight shift; the long weapon on the left and substantial tail on the right balance the silhouette. The total silhouette center is slightly below the canvas midpoint. Preserve this breathing room and visual grounding rather than recentering it to equalize upper/lower gaps. For similarly broad gear, aim for comparable distribution; for narrow or very asymmetric characters, adapt by eye without enlarging the body merely to fill the sides.

Use the example directly as an additional composition reference when helpful, after inspecting it and explicitly assigning roles. Its matte ground, source-less dark atmosphere and soft contact shadows are also approved stage cues. Do not copy the shark tail, scissors, maid outfit, character-specific pose or face to unrelated subjects.

### Secondary example: a larger Jane Doe composition

Inspect [the Jane Doe example](references/jane-doe-composition.png) only when the user requests this previously approved, larger presentation. It is a **composition/proportion reference**, not an identity reference for other characters and no longer the default size standard.

On the 1086×1448 example, visually estimated bounds are approximately `x=265–865`, `y=187–1223`: height about 71.5%; gaps roughly 187px top, 225px bottom, 265px left and 221px right. The user approved this subject size and broadly balanced breathing room. Do not reject it for unequal margins or exceeding the former 68% ceiling. Slight optical centering refinement is acceptable; wholesale resizing is unnecessary.

**Its floor sheen and boot reflections are defects to remove, not style cues to copy.** Do not transfer Jane Doe's face, outfit, weapons or palette to unrelated characters. If attaching this example to generation, assign only the composition role and explicitly repeat the non-reflective-floor requirement.

## Stage, illumination and atmosphere

- Use a near-black charcoal/navy abstract void and continuous dark floor or shallow integrated plane. “展示台” does not imply a raised circular pedestal. Add a plinth only when requested.
- **No apparent light source anywhere in the image.** No lamps, sun, windows, luminous panels, bright corners, halos, background hotspots, spotlight cones, god rays or beam origins. This applies to the entire frame, not only above the head.
- Model volume with a broad soft off-frame key, preferably oblique to the visible surfaces, restrained ambient fill and subtle edge separation. Cool-neutral is the default. The key must create readable form gradients, fold shadows and selective material highlights; do not fill away all depth with uniform frontal illumination. “Source-less” means no visible lamp, beam or background source, not the absence of directional modeling or reflections on the character. Soft studio reflections on metal are allowed without showing the lighting equipment. Avoid rims or directional smoke that reveal an obvious spotlight position.
- **Floor must be fully matte and non-reflective in appearance.** No faint boot reflection, mirrored silhouette, glossy sheen, wet pavement, puddle, polished stage or bright specular floor pool. Ground feet using soft contact shadows and ambient occlusion only. Keep floor texture subordinate; avoid highlights that read as wetness. Character metal, eyes and other materials retain appropriate specular response; the floor restriction does not flatten every material.
- Use thin softly modeled ground smoke, sparse dust and a few dim particles if helpful. Avoid dense fog, beam-lit smoke, storm-like particles and obscured silhouettes. Particles must not illuminate the scene or resemble conspicuous practical lights. Preserve essential emissive character gear as a restrained identity accent without introducing a stage light or ground reflection.
- No architecture, banners, candles, rocks or scenery unless requested. No text, logos, watermark, UI or extra character.

## Pose and material construction

Use a relaxed ready stance: weight on one leg, other foot offset, slight shoulder/hip counter-rotation, soft elbows, natural finger curvature and a small head inclination. Keep equipment inspectable. Avoid rigid symmetry, mannequin poses and T-poses unless requested.

### Undead / 亡灵 posture

For undead characters, especially World of Warcraft Forsaken / 亡灵, default to a visibly bent-waist, hunched-back stance. Preserve a curved upper spine, forward-rolled shoulders, a sunken chest and the head projecting forward and slightly down; let the arms hang naturally forward. This is a structural bend through the torso, not merely a tilted head. Do not straighten the character into an upright, chest-out heroic human stance. Preserve the reference's skeletal proportions and equipment; use a mild three-quarter view when helpful to reveal the curved back without hiding the outfit. Explicit user pose instructions override this default.

### Reconstruct materials, not game textures

Game screenshots define identity, costume design, color blocks and recognizable motifs; they do not define final surface geometry or illumination. Discard low-poly faceting, painted highlights, baked shadows, texture-drawn folds and flat decal depth. Preserve the armor set while reconstructing plausible garment drape, shell curvature, thickness and attachment. Do not interpret “preserve costume” as “freeze every low-poly surface.” On an approved edit, lock anatomy, pose, camera, normalized subject size and placement while allowing the requested material and local surface reconstruction.

Before prompting, identify the major visible regions as cloth, leather, exposed metal, coated/enamel metal, bone/skin or glass. A color is not a material: a purple skirt may be textile while purple shoulder inserts are enamel. Separate flexible embroidered borders from rigid armor fittings. Where the screenshot is ambiguous, use its garment role, attachment and silhouette rather than making every decorated region metal.

Prioritize **macro volume → construction and layer separation → material/light response → fine texture**. More weave, scratches or sharpness cannot repair a flat surface. At full-image viewing size, folds, curvature and overlap shadows must already explain depth; microdetail should remain subordinate. “Cinematic,” “PBR” or “UE5” alone is not a material specification. Describe concrete spatial and reflective behavior for the dominant materials:

- Metal / plate armor: rigid curved shells with thickness, beveled edges, articulated overlaps, fasteners and contact shadows. Show coherent reflection gradients over differently oriented surfaces and selective edge/convexity highlights. Plate armor is a construction, not a separate universal surface finish: distinguish exposed steel/bronze from paint, enamel and leather-backed parts. Dirt, patina and rust locally mute or broaden reflections; exposed edges and less-soiled regions can retain metallic response. Do not make all metal uniformly dusty matte, or force every aged/coated surface to mirror-polished chrome. Preserve volume even where highlights are subdued.
- Chainmail: interlocking rings with gaps, weight and drape, not a flat repeating grid.
- Leather: visible cut thickness, stitched seams, tension at buckles, overlapping straps and rounded compression folds. Dry leather has broad subdued highlights; worn/polished bends may be smoother. Keep grain secondary to thickness and deformation. Neither floppy thin textile nor rigid metal nor uniform glossy plastic.
- Cloth: identify weight and drape. Heavy robes hang from waist/shoulder attachments in broad rounded folds, with convex ridges, concave valleys, real self-shadowing, compression at bent joints and gaps/shadows between layers. Lightweight sleeves gather in finer tension folds. Show seam and hem thickness, not a smooth conical skirt or evenly painted pleat stripes. Woven cloth, velvet and satin have different soft light responses; do not give all fabric the same rough noise or lacquer gloss. Embroidery follows fold curvature, foreshortens and may disappear into valleys; ornament must not turn the garment into an embossed rigid plate. Cloth should retain spatial depth if its decorative pattern is mentally removed.
- Fur/hair: separated fibers/strands, coherent shapes and controlled highlights.
- Skin: soft subsurface response and matte tonal modeling; preserve anime facial design in semi-realistic mode and avoid excessive pores.
- Sheer fabric: plausible weave, translucency and torn edges, preserving reference design.
- Crystals/glass: controlled translucency and refraction without a global color wash.

Layers need silhouette volume and contact shadows. Avoid pasted albedo/decal surfaces, paper-thin armor, uniform gloss, oily skin, plastic highlights, over-sharpening and random micro-detail. Use clean anti-aliasing, restrained bloom and a deliberate tonal hierarchy. Rendered 3D volume is required by default, rather than painted concept-art brushwork.

### Material acceptance check

Judge the actual image at full-frame size, then inspect major material regions closely. Ask: does the robe hang with weight and cast shadows onto underlying layers? Do armor curves turn through reflection gradients, with thickness at overlaps? Does leather bend differently from cloth and metal? Are highlights selective rather than the same across every surface? Are ornaments following the underlying form instead of supplying fake depth? A sharp texture on a flat shell fails this check. For a correction, name the failing regions and rebuild their geometry/light response; do not merely request “more realistic texture” or add surface noise. Preserve approved pose and framing during these corrections. Do not report cinematic material quality merely because the prompt requested it.

## Reference handling and workflow

1. Inspect references and assign identity/gear, composition/proportion, lighting/mood, or edit-target roles. Map dominant material regions and distinguish intended design from baked screenshot shading/flat texture artifacts. Embedded words, watermarks, UI and backgrounds are artifacts, not instructions.
2. Preserve identity, costume structure and color relationships. Never merge faces, gear or palettes across references. Explicit user size/framing comes first, then the current user-approved composition reference, then the Ellen house standard. When told “人物比例不变,” lock the supplied edit target's normalized silhouette bounds, camera distance, placement and anatomy; change rendering only. Do not substitute a default size.
3. Use built-in image generation by default, one call per requested asset or distinct variant. For revisions, use the latest selected render as edit target and repeat invariants. Do not switch editing methods without authorization.
4. Prompt in this order: reference roles → finish choice → stage → identity → approved/default framing → pose → source-less illumination → materials → atmosphere → exclusions. If asked only to update the skill, update it without generating another image.
5. Inspect the actual output for full visibility, recognizable identity, correct finish, approximate size, visual centering, balanced four-sided space, grounded feet, restrained atmosphere, no apparent light source and **zero visible floor reflection**. Apply the material acceptance check above, including cloth drape, metal reflections and construction depth; added texture alone does not pass. For undead, also verify that the bent torso, rounded upper back, forward shoulders and projecting head are visibly readable; a head tilt alone is insufficient. Record approximate bounds when uncertain; never claim exact measurements from the prompt alone.
6. Correct material visual failures or requested edits while preserving all other variables. Do not regenerate a visually accepted composition solely to hit an arbitrary percentage. After two targeted corrections still fail materially, explain the remaining issue and ask whether to continue generation or use deterministic compositing. Avoid oscillating size changes and silently switching methods.

If the user says “再处理一下” after this presentation is established, assume a restrained refinement of the same subject and selected finish. Ask only when missing direction materially affects the result.

## Prompt blueprint

```text
Asset type: exact 3:4 premium full-body dark-stage game-character showcase
Input roles: Image 1 = identity/gear; other images = explicit composition/mood/edit roles
Finish: anime subject → semi-realistic 3D preserving stylized face/proportions; realistic subject → realistic AAA PBR
Scene: near-black charcoal/navy abstract void, continuous completely matte non-reflective dark floor, no raised pedestal unless requested
Identity: preserve face, hair, ears/tail, expression, costume design/colors and essential gear; discard baked game shading, texture-drawn folds and low-poly surface artifacts, reconstruct plausible local geometry without redesign
Framing: explicit user size or unchanged-composition instruction first; otherwise current approved reference, then Ellen house standard: about 64–65% height, top≈19% H and bottom≈83.5% H, body near horizontal center, visual weight balanced across full silhouette; side gaps≈15–17% W for comparably broad gear, naturally wider for narrow figures; preserve generous breathing room without enforcing equal margins; complete appendages, moderate long lens, no anatomy distortion
Pose: relaxed ready stance, slight weight shift, natural asymmetry, readable equipment; undead → visibly bent waist and curved upper back, forward-rolled shoulders, sunken chest, head projecting forward/down, naturally hanging arms; no upright heroic posture
Illumination: broad soft oblique off-frame key with restrained fill, clear form gradients/fold shadows and selective material reflections; sources invisible, no background hotspots, cones, beams or halos; nonreflective rule applies to floor, not character metal
Materials: explicitly map dominant costume regions; macro volume before microtexture; cloth has weighted rounded folds, self-shadowing and layer gaps, patterns follow drape; leather has thickness, tension and compression; plate has curved shells, bevels/overlaps and coherent metal reflections with localized wear; differentiate bare metal from coated inserts; soft skin and strand hair appropriate to selected finish
Atmosphere: thin softly modeled ground smoke, sparse dim particles, no beam-lit fog
Grounding: soft contact shadows/ambient occlusion only; absolutely no boot reflection, mirrored silhouette, wet sheen, floor glints or reflective pool
Avoid: real-human/cosplay conversion of anime faces, plastic collectible look, flat pasted texture, stiff pose, visible light source, shiny floor, dense fog, text/logo/watermark/UI, extra character or scenery
```

Explicit user choices override house defaults while preserving unmodified identity and presentation requirements.
