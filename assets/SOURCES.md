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

Nature A (2026-11-07, Ruben's Tripo models; masters on Drive, read only):

| File | Source | Used for |
|---|---|---|
| `models/nature/nature_a.glb` | Ruben's Tripo models, reduced by `tools/reduce_tripo.py` from the Drive masters listed below (Draco, JPEG 512 px base colour; nodes `<kind>_<n>` near + `<kind>_<n>_far` vertex-colour far LOD; far LODs rebuilt 2026-11-07 Nature B1 = decimated near mesh, trunk kept) | fill.js kinds oak, pine, pine_snow, dead, deadgrey, birch, blossom, giant_shroom, bush, rocks, boulder (3 variants each) |
| ↳ node `oak_1` | Tripo U6 "dark green round tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_10266bc6-397c-4e79-8fc6-9f0e86f026b6.glb` | fill kind `oak` variant 1 |
| ↳ node `oak_2` | Tripo U143 "dark oak tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_ef6cb455-6e6c-4ed6-97d5-1991e2b054e1.glb` | fill kind `oak` variant 2 |
| ↳ node `oak_3` | Tripo U78 "dark green twin-crown tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_8266d850-04df-455b-a4d5-212cee56382f.glb` | fill kind `oak` variant 3 |
| ↳ node `pine_1` | Tripo U21 "spruce pine tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_22fcd3ec-9428-43fa-8016-e7c1c6d6420f.glb` | fill kind `pine` variant 1 |
| ↳ node `pine_2` | Tripo U106 "spruce pine tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_ad768096-2b54-46e5-b277-361ebd009d08.glb` | fill kind `pine` variant 2 |
| ↳ node `pine_3` | Tripo U35 "pine tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_3cd7beb1-bd60-4c50-9a6a-cceee217b679.glb` | fill kind `pine` variant 3 |
| ↳ node `pine_snow_1` | Tripo U102 "snowy pine tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_a7171493-8969-424a-afb3-c34778330866.glb` | fill kind `pine_snow` variant 1 |
| ↳ node `pine_snow_2` | Tripo U104 "snowy pine tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_a990c8d3-c5a7-4278-8b49-a7e2785dc1c7.glb` | fill kind `pine_snow` variant 2 |
| ↳ node `pine_snow_3` | Tripo U122 "snowy pine tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_cacfad4b-0d88-4f2a-af9f-743c8062c75e.glb` | fill kind `pine_snow` variant 3 |
| ↳ node `dead_1` | Tripo U7 "gnarled bare twisted tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_10b6bbf2-454b-4e3c-a537-1c32df4abfc5.glb` | fill kind `dead` variant 1 |
| ↳ node `dead_2` | Tripo U45 "bare branching dead tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_4f43dd93-45f4-4cd5-9e41-5b02bb9f648b.glb` | fill kind `dead` variant 2 |
| ↳ node `dead_3` | Tripo U99 "gnarled dead tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_a2fbd731-b9ea-4ae2-b8c7-f9971eaac928.glb` | fill kind `dead` variant 3 |
| ↳ node `deadgrey_1` | Tripo U38 "dead dark twisted spooky tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_41f46878-c32b-479e-9007-7d744f409bba.glb` | fill kind `deadgrey` variant 1 |
| ↳ node `deadgrey_2` | Tripo U111 "dark dead tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_b57d8525-dbf7-4ae7-a4cd-f9beb440a77f.glb` | fill kind `deadgrey` variant 2 |
| ↳ node `deadgrey_3` | Tripo U125 "dead tree with hollow": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_d1d3a34c-ddb5-4058-a23f-d7f5769ad762.glb` | fill kind `deadgrey` variant 3 |
| ↳ node `birch_1` | Tripo U5 "birch tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_0ffaae06-04e6-4bda-a734-e6ec44ec65fe.glb` | fill kind `birch` variant 1 |
| ↳ node `birch_2` | Tripo U81 "birch tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_85e2d198-20c6-4408-944a-0567639a81c6.glb` | fill kind `birch` variant 2 |
| ↳ node `birch_3` | Tripo U57 "tall narrow birch-willow tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_5d93326a-1a83-4846-9291-f0898db4808e.glb` | fill kind `birch` variant 3 |
| ↳ node `blossom_1` | Tripo U37 "pink blossom tree": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_3f29fced-2bee-4521-aa4e-dfefd505a416.glb` | fill kind `blossom` variant 1 |
| ↳ node `blossom_2` | Tripo U28 "blue-violet tree with pink blossoms": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_2ec56a42-de9b-4482-ad58-88979ff21db5.glb` | fill kind `blossom` variant 2 |
| ↳ node `blossom_3` | Tripo U129 "flowering tree with white blossoms and vines": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_d50873b3-3920-44fb-a26b-55ab8e3c89e2.glb` | fill kind `blossom` variant 3 |
| ↳ node `giant_shroom_1` | Tripo U3 "teal spotted mushroom (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_09c8c3e2-41bb-40d8-acca-1e58ffd311c4.glb` | fill kind `giant_shroom` variant 1 |
| ↳ node `giant_shroom_2` | Tripo U74 "green spotted mushroom (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_7c0b42de-13fe-4886-a690-863d87efb3e1.glb` | fill kind `giant_shroom` variant 2 |
| ↳ node `giant_shroom_3` | Tripo U140 "pink flower-cap mushroom (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_eca8ebae-9043-4f51-a3df-da58bef8e393.glb` | fill kind `giant_shroom` variant 3 |
| ↳ node `bush_1` | Tripo U2 "leafy green bush": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_04af0f5d-fb7b-4c23-882b-d443a59440e5.glb` | fill kind `bush` variant 1 |
| ↳ node `bush_2` | Tripo U12 "broad-leaf dark green bush": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_1837ec05-f9a9-4f14-8111-d92840d6dfb8.glb` | fill kind `bush` variant 2 |
| ↳ node `bush_3` | Tripo U48 "green leafy bush": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_52e8f565-1495-419e-a96a-af83c04e25aa.glb` | fill kind `bush` variant 3 |
| ↳ node `rocks_1` | Tripo U16 "grey boulders with grass": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_1c38d9d4-8838-4281-96e6-ea5506918835.glb` | fill kind `rocks` variant 1 |
| ↳ node `rocks_2` | Tripo U18 "stacked grey rocks": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_1ee90eea-5079-4009-8aba-b5da98b7c4a7.glb` | fill kind `rocks` variant 2 |
| ↳ node `rocks_3` | Tripo U154 "stacked mossy rocks": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_fe2ad834-ce71-4bbf-89d6-d43e4fa09d11.glb` | fill kind `rocks` variant 3 |
| ↳ node `boulder_1` | Tripo U23 "flat grey rock slabs": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_264d1d64-9f89-4fea-9698-f14edc96e92c.glb` | fill kind `boulder` variant 1 |
| ↳ node `boulder_2` | Tripo U70 "mossy rock": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_773c7dbe-6e37-4f21-a16e-9b837e29b7c6.glb` | fill kind `boulder` variant 2 |
| ↳ node `boulder_3` | Tripo U88 "tall mossy rock": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_8baaf1ba-01aa-4739-ac0c-09fd63aa0e3f.glb` | fill kind `boulder` variant 3 |

Nature B1 (2026-11-07, Ruben's Tripo models; masters on Drive, read only; job list `review/tripo_map/job_nature_b1.csv`):

| File | Source | Used for |
|---|---|---|
| `models/nature/nature_b.glb` | Ruben's Tripo models, reduced by `tools/reduce_tripo.py` (Draco, JPEG base colour 512 px cactus / log / bleached / rotthorns with 1.5k near + 250 far; 256 px shroom / fern / lily / reed / glowshroom ~500 near, no far node) | fill.js kinds cactus, log, bleached, shroom, fern, lily, reed, rotthorns, glowshroom (2-3 variants each) |
| ↳ node `cactus_1` | Tripo U150 "saguaro cactus": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_f35b8dcd-b9dd-4f7c-bffa-781faa9ebcfa.glb` | fill kind `cactus` variant 1 |
| ↳ node `cactus_2` | Tripo U24 "prickly pear cactus with red flower": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_28f6a0d1-2aab-434d-abfe-23c79a11ee69.glb` | fill kind `cactus` variant 2 |
| ↳ node `cactus_3` | Tripo U4 "barrel cactus with red flower": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_0a5dca9e-86b1-44a8-8923-97bc530cceed.glb` | fill kind `cactus` variant 3 |
| ↳ node `log_1` | Tripo U79 "branch log with stubs": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_833eab30-f15b-4617-af9c-48aab80c81a3.glb` | fill kind `log` variant 1 |
| ↳ node `log_2` | Tripo U126 "tan hollow log with small carving": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_d2332f61-36d5-4486-9a9e-cf088bcda62a.glb` | fill kind `log` variant 2 |
| ↳ node `bleached_1` | Tripo U148 "beige rocks": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_f18e4065-a2f5-47c4-bee4-90404afdeff7.glb` | fill kind `bleached` variant 1 |
| ↳ node `bleached_2` | Tripo U96 "red rock mesa hoodoo": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_9d5c2c6d-bfc2-45ed-970a-07cf6823e564.glb` | fill kind `bleached` variant 2 |
| ↳ node `bleached_3` | Tripo U105 "red rock formation": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_ab3b9f9d-43d9-4f2e-bb8d-4d1c86dc5021.glb` | fill kind `bleached` variant 3 |
| ↳ node `shroom_1` | Tripo U84 "brown cap mushrooms (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_88908bce-bb25-4ae8-ae9f-576847e0e121.glb` | fill kind `shroom` variant 1 |
| ↳ node `shroom_2` | Tripo U115 "chanterelle cluster (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_b99773e1-4110-43fb-b5b9-df3dfed4c227.glb` | fill kind `shroom` variant 2 |
| ↳ node `shroom_3` | Tripo U55 "orange mushroom cluster (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_5c6410ed-e9f7-4bf3-8b24-a2b18eeed6af.glb` | fill kind `shroom` variant 3 |
| ↳ node `fern_1` | Tripo U30 "fern": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_2f6522b3-f51e-4e28-874d-a16625cadc50.glb` | fill kind `fern` variant 1 |
| ↳ node `fern_2` | Tripo U53 "dark fern": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_5a7e5ff3-bad5-4445-87a4-164651e173f0.glb` | fill kind `fern` variant 2 |
| ↳ node `lily_1` | Tripo U119 "plain lily pad": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_c15859d4-e458-4c7c-903b-ca10cf027777.glb` | fill kind `lily` variant 1 |
| ↳ node `lily_2` | Tripo U15 "blue water lily": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_1c1a1829-43cb-4b60-87ef-49138728476c.glb` | fill kind `lily` variant 2 |
| ↳ node `lily_3` | Tripo U127 "white lotus": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_d2e6f0ad-6f9d-4bb7-9162-5ddb81382e62.glb` | fill kind `lily` variant 3 |
| ↳ node `reed_1` | Tripo U8 "cattails (water plant)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_11adf54f-0f2f-4fe8-87d3-79dc9621a03a.glb` | fill kind `reed` variant 1 |
| ↳ node `reed_2` | Tripo U43 "cattails (water plant)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_480f8533-ce48-43a0-9b4b-097d7acf8827.glb` | fill kind `reed` variant 2 |
| ↳ node `reed_3` | Tripo U71 "single cattail (water plant)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_77a142f7-e904-477f-aeec-28ae01a2e3a4.glb` | fill kind `reed` variant 3 |
| ↳ node `rotthorns_1` | Tripo U116 "thorny bramble bush": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_ba73fc7d-2fe3-4c0e-a810-ceb6679d02b0.glb` | fill kind `rotthorns` variant 1 |
| ↳ node `rotthorns_2` | Tripo U91 "dry dead twig brush": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_96df3ed3-4ef5-4667-a004-dde3910a1ea2.glb` | fill kind `rotthorns` variant 2 |
| ↳ node `glowshroom_1` | Tripo U68 "plain purple mushroom (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_70cb0f8a-e769-41dd-8684-b3cb4d95347c.glb` | fill kind `glowshroom` variant 1 |
| ↳ node `glowshroom_2` | Tripo U95 "purple mushroom trio (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_9b7cfc15-bb2b-4e35-a10b-a96a65b3b9af.glb` | fill kind `glowshroom` variant 2 |
| ↳ node `glowshroom_3` | Tripo U153 "purple spotted mushroom (mushroom)": `G:/My Drive/3D Assets/Downloads/Unsorted/tripo_convert_fa63915f-ca78-4fd6-ae6a-f5e3b34e1282.glb` | fill kind `glowshroom` variant 3 |
