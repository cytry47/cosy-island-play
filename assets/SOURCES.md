# Asset sources

All from the Pupkins Hub fetch (`Ruben HQ/Asset Library/moku/pupkins-hub/`, pupkins.moku.gg, fetched 2026-10-26; Moku-approved IP, not CC0). Copied unchanged.

| File | Source | Used for |
|---|---|---|
| `models/Moki_Base.glb` | `moki-sdk/assets/models/base/Moki_Base.glb` (clips Idle, Run, Kick, Stun) | player body; idle + run clips |
| `models/moki-clips.glb` | `whale-hub/dev/avatars/moki-clips.glb` (PSPS_* clips, same bone names) | player walk clip (PSPS_Walk) |
| `models/schiffy.glb` | `schiffy/schiffy.glb` (clips PSPS_Idle, PSPS_Run) | pet Schiffy; idle + run |
| `models/schiffy-clips.glb` | `whale-hub/dev/avatars/schiffy-clips.glb` | pet walk clip (PSPS_Walk) |
| `models/props.glb` | `whale-hub/props.glb` (Draco; nodes prop_<kind>) | trees, pines, bushes, rocks, lanterns, bench, barrel, crate |
| `tex/grass_albedo.webp` | `pup-home/farm/tex/grass_albedo.webp` | island grass (tinted per vertex) |
| `tex/soil_albedo.webp` | `pup-home/farm/tex/soil_albedo.webp` | farm bed soil (tinted dry / damp) |

`public/draco/` = the Draco decoder copied from `node_modules/three/examples/jsm/libs/draco/gltf/` (MIT, three.js).
The island ground mesh, stone cliff, beach, foam, sea, sky, flowers are made in code (`src/render/island.js`).
Farm bed planks, soil ridges and all crops (carrot, blueberry, pumpkin; sprout/mid/ripe) are made in code (`src/render/farm.js`):
the Pupkins farm GLBs (`pup-home/farm/lite|reuse|village-far.glb`) hold no crop meshes.
HUD crop icons are rendered at startup from those crop models (`renderCropIcons` in `src/render/farm.js`), no image files.
HUD font = Fredoka via the `@fontsource/fredoka` npm package (SIL OFL), bundled by Vite, no CDN.

House (job 4):

| File | Source | Used for |
|---|---|---|
| `models/reuse.glb` | `pup-home/farm/reuse.glb` (Pupkins Hub, Draco; nodes portal_small, cottage_shell, cottage_awning, workbench) | island house = `cottage_shell` only (scaled x4.6; its emissive map is carried into the toon material) |
| `models/furniture/bedSingle.glb`, `tableCloth.glb`, `chairCushion.glb`, `rugRounded.glb`, `lampRoundFloor.glb`, `pottedPlant.glb` | `Asset Library/kenney/furniture-kit/Models/GLTF format/` (Kenney, CC0) | NOT USED since job 4 r2 (hard-edged next to Pupkins; furniture is now code-built in `src/render/furniture.js`). Delete pending Ruben's OK. |

The interior room (plank floor, walls, posts, beams, window, door, doormat) and all furniture are made in code (`src/render/house.js`); the wall lantern is `prop_hanging_lantern` from `props.glb`.

World (build step 1):

| File | Source | Used for |
|---|---|---|
| `tex/stone_albedo.webp` | `pup-home/farm/tex/stone_albedo.webp` (Pupkins Hub) | terrain: cliffs, mountain, magic-isle moss (blended per vertex) |
| `models/props_lod.glb` | `Games/Web/last-pup-standing/assets/props/forest/props_lod.glb` (LPS 25, simplified from Pupkins `props.glb`) | far LOD of tree_round, pine, bush, rocks fill |
| `models/trees.glb` | `Asset Library/ours/pawty/trees.glb` (ours, accepted 2026-10-30) | fill trees: oak, birch, dead, pinesnow, blossom, mushroom a/b |
| `models/enemies/fantasy_boar.glb` | Ruben's Tripo model (Drive `3D Assets/Cosy Island/Enemies/fantasy boar 3d model.glb`, 2026-11-06) | job 7 boar look (`render/combat.js` swapBoarGlb), trial |

Terrain chunks, sea / river / lake / bog water, grass clumps, flowers, glow flowers, bridge stubs and the far island silhouettes are made in code (`src/render/terrain.js`, `water.js`, `fill.js`, `island.js`).

Animations (2026-11-07):

| File | Source | Used for |
|---|---|---|
| `models/moki-kaykit-clips.glb` | KayKit Character Animations 1.1 (Kay Lousberg, CC0; `Asset Library/kaykit-animations/`, Rig_Medium packs), retargeted onto the Moki armature by `tools/retarget_kaykit.py` (armature only, no mesh; 62 clips `Moki_<KayKitName>`) | Moki combat / bow / magic / tool / fishing / sit / lie / hit / death clips (not wired into the game yet) |
