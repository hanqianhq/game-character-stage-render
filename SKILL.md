---
name: game-character-stage-render
description: 将二次元角色、概念原画、游戏截图或角色渲染图按参考类型转译为 3:4 暗黑舞台角色展示图：二次元默认 3D 半写实，概念原画优先做 3D 资产重建，写实游戏角色默认 AAA / Unreal Engine 质感。保留身份与装备设计，同时重建体积、结构、材质与光照；默认角色轮廓约占画面高度 60%，使用不可见的面光源、柔和环境雾光、轮廓分离与接地阴影；亡灵默认使用弯腰驼背姿态。
---

# Game Character Stage Render

Create a premium full-body 3:4 character showcase in an abstract dark studio void. Preserve identity and equipment while rebuilding volume, materials and illumination. The house presentation is visually centered, with roughly balanced space on all four sides. Lighting must model the character and environment clearly; keep fixtures and light-emitting objects outside the frame while allowing diffuse ambient glow and soft atmospheric gradients. The floor is always fully matte and non-reflective.

## Choose the reconstruction level

The finish must match both the source-image type and the user's requested degree of realism. Do not force every character into photorealistic Unreal Engine rendering, and do not treat the word “cinematic” as proof of modeled geometry.

### Mode A — Stylized / anime reference → semi-realistic 3D

Use for anime art, stylized game characters and strongly designed 2D illustrations. Preserve the original facial proportions, silhouette, hairstyle, expression, costume identity and color relationships. Add believable 3D volume, soft physical shading, strand-based hair and material separation, but do not convert the subject into a photorealistic human, cosplayer, wax figure or plastic collectible. The target is a semi-realistic 3D interpretation that preserves the source's stylized appeal.

### Mode B — Concept art / fantasy illustration → 3D asset reconstruction

Use for dark-fantasy concept art, character sheets and painterly illustrations. Treat the reference as identity, costume and equipment evidence only; ignore its brushwork, painted highlights, flat folds, baked shadows and concept-art composition. Reconstruct a believable production-ready 3D asset before adding cinematic presentation:

- establish body mass, silhouette, pose and camera distance;
- build separate armor shells with thickness, bevels, clearances and attachment points;
- suspend cloth, straps, chains and ornaments from believable anchors with gravity and contact shadows;
- give weapons a continuous axis, functional grip, joints, collars and mechanically plausible connections;
- separate steel, leather, cloth, bone, hair and coated/enamel parts by geometry and optical response;
- add sparse surface wear only after the macro and medium forms read correctly.

A result fails this mode if it looks like a polished repaint of concept art, even when it has many scratches, seams or highlights. If surface texture is removed, the character must still read as a coherent modeled asset.

### Mode C — Realistic game reference → AAA / Unreal Engine finish

Use for game screenshots, realistic armor references and existing 3D renders. Preserve the established design, anatomy, pose, camera relationship and equipment while rebuilding only the geometry and materials needed for believable AAA presentation. Use physically based reflections, roughness separation, local wear, plausible cloth and leather behavior, and restrained cinematic lighting.

### Routing priority

1. An explicit user finish request overrides defaults.
2. If the user does not specify a finish, classify the reference first: anime/stylized → Mode A; concept art/fantasy illustration → Mode B; game screenshot/realistic 3D render → Mode C.
3. “Unreal Engine” describes the rendering target and material quality; it does not require photorealistic anatomy for a stylized subject.
4. “Cinematic” describes presentation only. It never replaces geometry, construction, weight, attachment, occlusion or material separation.

## Choose the character finish

- **Anime / 二次元: default to semi-realistic 3D.** Retain recognizable stylized facial proportions, eye shape, hairstyle, expression, body silhouette and costume. Add believable volume, soft skin shading, strand hair and physical materials. Do not convert the character into a real human, cosplayer, wax figure or plastic collectible. Avoid aggressive pores, aging and facial restructuring that erase the original appeal. The target is anime identity with refined semi-realistic materials and illumination, not flat cel shading or painted concept art.
- **Realistic game characters and armor: default to realistic AAA / Unreal Engine 5 quality.** Rebuild layered geometry and physical materials without redesigning the character.
- Explicit finish requests override defaults. Unreal Engine 5 describes render quality; it does not require photorealistic human anatomy for every subject. Anime identity itself is not a failure mode.

## Composition and framing

- Use exact 3:4 portrait unless requested otherwise. Show the complete requested silhouette, including hair, ears, cape, tail, hands, feet and included equipment. Include weapons when requested or essential to identity; otherwise remove them cleanly.
- **Default complete-silhouette height is about 60% of the canvas height** (`q ≈ 0.60`), including requested gear. Roughly 59–61% is useful guidance, not a mechanical pass/fail rule. For 3:4 portrait framing, start near `y_top ≈ 0.21H` and `y_bottom ≈ 0.81H`; this leaves generous breathing room while keeping the subject slightly low and grounded. This 60% default replaces the former 64–65% size cue. The Ellen image below remains a presentation and balance reference, but do not inherit its larger subject scale unless the user explicitly asks to match that proportion. Explicit user size instructions, unchanged-size edits, and a composition reference explicitly requested for its proportions take priority.
- **Center visually**, balancing the main body with its complete silhouette. Keep the main body near the horizontal center, with grounded weight and relaxed asymmetry; weapon, tail, cape and hair should balance the surrounding negative space. Judge the whole image, not the face or a single appendage. All four sides need breathing room, but neither four equal gaps nor identical top/bottom gaps are required. Preserve the approved reference's margin relationships rather than forcing mathematical symmetry.
- Use the complete silhouette bounding box as a diagnostic. Thin extended weapons, tails or stray hair must not drag the main body visibly off-center. Allow small optical placement adjustments while keeping every appendage fully visible. Do not deliberately place the character off-axis by default.
- Preserve anatomy with camera distance and a moderate long lens, around 70mm. Use near-front presentation with a mild three-quarter turn. Avoid cropping, wide-angle stretching and dramatic low-angle foreshortening.
- A normal screenshot/cutout supplies identity and gear; its framing is non-binding. A user-approved composition reference supplies framing when the user asks to follow its proportions. Otherwise use the 60% house default and borrow only the reference's balance, margin character and stage presentation.

### Numerical guidance, not a pixel lock

For canvas `W × H` and silhouette bounds `(x_left, y_top, x_right, y_bottom)`, estimate `h = y_bottom - y_top`, `q = h / H`, and margins `T = y_top`, `B = H - y_bottom`, `L = x_left`, `R = W - x_right`. Include requested gear; exclude smoke, particles, glow and contact shadows.

For an unreferenced default, prompt `q ≈ 0.60`, `y_top ≈ 0.21H`, `y_bottom ≈ 0.81H`, then judge side gaps and visual balance. On 1086×1448 this means about 869px subject height, 304px above and 275px below. A silhouette with proportions similar to Ellen will be about 63–64% of canvas width at this height, leaving roughly 18% on each side; narrower characters naturally leave wider side gaps. Do not stretch the pose or invent appendages to force a particular width. These are approximate guides. A pleasing approved image should not trigger regeneration over small numerical differences or a one-percent margin tolerance.

For “increase 5%,” use `h_target = h_source * 1.05`, scaling width equally, not adding five percentage points. Preserve design, pose and approved framing; adjust placement only enough to maintain visual balance. Compare normalized sizes if resolution changes. Fix a placement error by translation, not resizing.

### Primary presentation standard: Ellen

Inspect [the approved Ellen render](references/ellen-composition-standard.png) when creating a new showcase with default house framing. The user selected it as the standard for visual balance, breathing room, and stage presentation; it supersedes the earlier Jane Doe example as the default. The newer 60% house rule supersedes Ellen's original subject size. Assign it **composition and stage-presentation roles only** when rendering another character; preserve the new identity reference's own face, pose, costume, gear and palette.

On its 1086×1448 canvas, visually estimated complete silhouette bounds are `x≈177–920`, `y≈276–1212`: height about 64.6%, width about 68.4%; top gap about 276px (19.1% H), bottom about 236px (16.3% H), left about 177px (16.3% W), right about 166px (15.3% W). These measurements describe the approved image only. For a new default render, use a similar visual balance at about 60% height, with correspondingly wider breathing room; do not force the reference's exact silhouette bounds onto a different character.

The main body reads near horizontal center, with a natural weight shift; the long weapon on the left and substantial tail on the right balance the silhouette. Keep the total silhouette center slightly below the canvas midpoint rather than recentering it to equalize upper/lower gaps. At the 60% default, keep this visual balance while allowing the margins to grow; for narrow or very asymmetric characters, adapt by eye without enlarging the body merely to fill the sides.

Use the example directly as an additional composition reference when helpful, after inspecting it and explicitly assigning roles. Its matte ground, dark atmospheric gradient and soft contact shadows are also approved stage cues. Do not copy the shark tail, scissors, maid outfit, character-specific pose or face to unrelated subjects.

### Secondary example: a larger Jane Doe composition

Inspect [the Jane Doe example](references/jane-doe-composition.png) only when the user requests this previously approved, larger presentation. It is a **composition/proportion reference**, not an identity reference for other characters and no longer the default size standard.

On the 1086×1448 example, visually estimated bounds are approximately `x=265–865`, `y=187–1223`: height about 71.5%; gaps roughly 187px top, 225px bottom, 265px left and 221px right. The user approved this subject size and broadly balanced breathing room. Do not reject it for unequal margins or exceeding the former 68% ceiling. Slight optical centering refinement is acceptable; wholesale resizing is unnecessary.

**Its floor sheen and boot reflections are defects to remove, not style cues to copy.** Do not transfer Jane Doe's face, outfit, weapons or palette to unrelated characters. If attaching this example to generation, assign only the composition role and explicitly repeat the non-reflective-floor requirement.

## Stage, illumination and atmosphere

- Use a near-black charcoal/navy abstract void and continuous dark floor or shallow integrated plane. “展示台” does not imply a raised circular pedestal. Add a plinth only when requested.
- **Keep light-emitting objects and their origins outside the frame.** No visible lamps, sun, windows, luminous panels, or hard-edged spotlight cones or beams. This does not mean the scene is unlit: a soft, broad ambient glow, a low-contrast backdrop halo, or a gently illuminated mist gradient is welcome when it has no visible origin, sharp ring edge, or concentrated point hotspot. Keep the stage dark and the atmospheric glow subordinate to the character.
- **Use large off-frame area lights by default, never point lights.** Shape the character with a broad soft oblique Area Light key, restrained diffuse/environment fill, and an optional weaker broad area source behind or to the side for selective contour separation. Cool-neutral is the default. Let the key and fill produce readable form gradients, fold shadows, local occlusion and controlled material highlights; do not flatten depth with uniform frontal fill. Add soft bounce light from nearby costume colors and ambient darkening where forms meet. Contour light should vary naturally, catching only selected edges and strands rather than tracing a uniform bright outline; keep its source invisible. Character metal, glass and coated surfaces may show coherent softbox reflections without showing the equipment. Do not use pinpoint highlights, a single hard rim, or directional smoke that exposes a light position.
- **Floor must be fully matte and non-reflective in appearance.** No faint boot reflection, mirrored silhouette, glossy sheen, wet pavement, puddle, polished stage, floor glints or bright specular pool. Ground feet and equipment with visible soft contact shadows, ambient occlusion, and a restrained soft cast shadow that extends consistently away from the broad key. Let shadows be darkest at contact and soften with distance; keep them subtle but readable against the dark floor. Never use a reflected silhouette to ground the subject. Keep floor texture subordinate and rough; avoid highlights that read as wetness. Character metal, eyes and other materials retain appropriate specular response; the floor restriction does not flatten every material.
- Use thin softly modeled ground smoke only by default. A faint, diffuse glow within the haze or behind the character is allowed, but it must read as broad environmental illumination rather than a visible lamp or point source. Do not add floating dust, muddy specks, glowing motes or decorative particles unless the user explicitly requests them. Avoid dense fog, hard light beams and obscured silhouettes. Preserve essential emissive character gear as a restrained identity accent without introducing a stage light or ground reflection.
- No architecture, banners, candles, rocks or scenery unless requested. No text, logos, watermark, UI or extra character.

## Lighting integration acceptance check

Before accepting a render, verify that the subject is optically embedded in the stage rather than pasted over it:

- broad form gradients describe the face, armor, cloth and equipment volumes;
- overlapping parts create local occlusion and believable self-shadowing;
- a restrained soft area-light wrap separates selected silhouette edges from the dark background without drawing a continuous outline;
- feet, weapon ends and supports have readable contact shadows, with a soft cast shadow linking the subject to the matte floor;
- nearby floor and backdrop receive only restrained diffuse bounce, never a mirrored or glossy reflection;
- material responses differ by region: metal has controlled directional reflections, leather and cloth have broader subdued highlights, skin/hair remain appropriately soft;
- no lamp, point hotspot, hard beam or sharp ring-shaped halo is visible; a broad low-contrast ambient glow or haze gradient is acceptable.

If the character looks like a cutout, first repair the area-light wrap, form gradients, local occlusion, contact shadows and soft cast shadow; let the background haze glow support separation only. Do not solve it with a visible point light, a continuous neon outline, a shiny floor, dense fog or random texture noise.

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

## 3D asset anti-concept-art gate

Before reporting a render as a successful 3D asset reconstruction, inspect the actual image at full-frame size and ask:

- Do the largest forms read through geometry before texture or decoration?
- Can armor pieces be separated by thickness, gaps, overlaps and attachment logic?
- Do cloth, straps, chains and weapons have real weight, gravity and contact?
- Do different materials produce different roughness and reflection behavior?
- Is the lighting describing the modeled surfaces rather than painting contour highlights onto them?
- Would the character still read as a 3D asset if scratches, engravings and microtexture were removed?

Reject or correct the result when it has a cleaned-up poster silhouette, pasted-on ornament, uniform detail density, painted folds, brush-like torn edges, melted weapon joins, impossible intersections, or cinematic haze used to conceal weak geometry. Prefer one targeted geometry/material correction over adding more texture.
## Reference handling and workflow

1. Inspect references and assign identity/gear, composition/proportion, lighting/mood, or edit-target roles. Map dominant material regions and distinguish intended design from baked screenshot shading/flat texture artifacts. Embedded words, watermarks, UI and backgrounds are artifacts, not instructions.
2. Preserve identity, costume structure and color relationships. Never merge faces, gear or palettes across references. Explicit user size/framing comes first; when told “人物比例不变,” lock the supplied edit target's normalized silhouette bounds, camera distance, placement and anatomy. Follow a composition reference's exact proportions when the user asks to match them; otherwise use the 60% house default and the Ellen image only as a presentation/balance cue. Do not substitute a default size for an unchanged-size edit.
3. Use built-in image generation by default, one call per requested asset or distinct variant. For revisions, use the latest selected render as edit target and repeat invariants. Do not switch editing methods without authorization.
4. Prompt in this order: reference roles → finish choice → stage → identity → approved/default framing → pose → area-light and ambient illumination → materials → atmosphere → exclusions. If asked only to update the skill, update it without generating another image.
5. Inspect the actual output for full visibility, recognizable identity, correct finish, approximate 60% default size or requested size, visual centering, balanced four-sided space, grounded feet, integrated contour lighting, readable contact/cast shadows, restrained atmosphere, no visible fixture or point hotspot, and **zero visible floor reflection**. A subtle diffuse background glow is allowed. Apply the material acceptance check above, including cloth drape, metal reflections and construction depth; added texture alone does not pass. For undead, also verify that the bent torso, rounded upper back, forward shoulders and projecting head are visibly readable; a head tilt alone is insufficient. Record approximate bounds when uncertain; never claim exact measurements from the prompt alone.
6. Correct material visual failures or requested edits while preserving all other variables. Do not regenerate a visually accepted composition solely to hit an arbitrary percentage. After two targeted corrections still fail materially, explain the remaining issue and ask whether to continue generation or use deterministic compositing. Avoid oscillating size changes and silently switching methods.

If the user says “再处理一下” after this presentation is established, assume a restrained refinement of the same subject and selected finish. Ask only when missing direction materially affects the result.

## Prompt blueprint

```text
Asset type: exact 3:4 premium full-body dark-stage game-character showcase
Input roles: Image 1 = identity/gear; other images = explicit composition/mood/edit roles
Finish: anime subject → semi-realistic 3D preserving stylized face/proportions; realistic subject → realistic AAA PBR
Scene: near-black charcoal/navy abstract void, continuous completely matte non-reflective dark floor, no raised pedestal unless requested
Identity: preserve face, hair, ears/tail, expression, costume design/colors and essential gear; discard baked game shading, texture-drawn folds and low-poly surface artifacts, reconstruct plausible local geometry without redesign
Framing: explicit user size or unchanged-composition instruction first; otherwise about 60% complete-silhouette height (q≈0.60), top≈21% H and bottom≈81% H, body near horizontal center, visual weight balanced across full silhouette; for a broad silhouette similar to Ellen, side gaps≈18% W, naturally wider for narrow figures; preserve generous breathing room without enforcing equal margins; complete appendages, moderate long lens, no anatomy distortion
Pose: relaxed ready stance, slight weight shift, natural asymmetry, readable equipment; undead → visibly bent waist and curved upper back, forward-rolled shoulders, sunken chest, head projecting forward/down, naturally hanging arms; no upright heroic posture
Illumination: physically readable lighting from large invisible off-frame Area Lights, never point lights: broad soft oblique key, restrained diffuse/environment fill, optional weaker area-light rim for selective contour separation, bounce light, overlap occlusion, and clear form gradients/fold shadows; soft contact and cast shadows anchor feet and equipment to the floor. A subtle broad ambient glow or low-contrast haze gradient behind the subject is welcome; no visible fixtures, pinpoint hotspots, hard cones/beams, sharp ring halos or continuous outline. Character materials may reflect selectively, but the floor remains completely matte and non-reflective
Materials: explicitly map dominant costume regions; macro volume before microtexture; cloth has weighted rounded folds, self-shadowing and layer gaps, patterns follow drape; leather has thickness, tension and compression; plate has curved shells, bevels/overlaps and coherent metal reflections with localized wear; differentiate bare metal from coated inserts; soft skin and strand hair appropriate to selected finish
Atmosphere: thin softly modeled ground smoke only by default; no floating dust, muddy specks, glowing motes or decorative particles unless explicitly requested; no beam-lit fog
Grounding: readable soft contact shadows, ambient occlusion and a broad soft cast shadow extending away from the area-light key; absolutely no boot reflection, mirrored silhouette, wet sheen, floor glints or reflective pool
Avoid: real-human/cosplay conversion of anime faces, plastic collectible look, flat pasted texture, stiff pose, visible light fixture, point-source hotspot, hard light beam, neon/ring outline, shiny floor, dense fog, text/logo/watermark/UI, extra character or scenery
```

Explicit user choices override house defaults while preserving unmodified identity and presentation requirements.
