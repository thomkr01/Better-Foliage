# TchicX's Better Foliage: notes for Claude

Minecraft Java resource pack by TchicX: random plant variants, bushy leaves. Plants only.

**Keep this file up to date.** Whenever TchicX makes a decision, changes a convention or asks for something to be done a certain way, add or update it here in the same commit.

## Current state

- Version: **6.2.0** (in `pack.mcmeta` description, README badge, `CHANGELOG.md`)
- Minecraft 26.1 – 26.3, pack format `min_format` 84, `max_format` 97.1
- Poplar leaves only exist from 26.3

## Layout

- `pack.mcmeta`, `pack.png` (320×320 pixel-art oxeye daisy on grass, built from `oxeye_daisy_small.png` on a 20×20 grid scaled ×16)
- `assets/minecraft/blockstates`, `models/block`, `models/item`, `textures/block`, `textures/entity/cow`
- `assets/minecraft/optifine/`: Continuity-format files (sugar cane connected textures, `emissive.properties` for glow lichen `_e` textures)
- `assets/cullleaves/options/options.json`: settings read by the Cull Leaves mod (see Background). Not a model or blockstate, so no credit label.
- `README.md`, `CHANGELOG.md` (not included in the release zip)

## Rules

- **Credit label**: every model and blockstate JSON starts with `"credit": "Made by TchicX for TchicX's Better Foliage"`. `.properties` files get it as a `#` comment. Skip `.png.mcmeta` files.
- **JSON layout**: 4-space indent, short objects and arrays kept on one line.
- **No visual change unless asked**: for tidy-ups, prove it (see Verifying below).
- **Blockstate variant lists**: use one `""` key when every state shares the list. Merging identical entries is only safe when they're next to each other (sum the weights).

## Deliberate choices (don't "fix" these)

- `blockstates/oak_leaves.json` keeps separate `distance=1` weights: leaves next to logs are slightly less bushy on purpose.
- `models/block/leaves_bushy.json` keeps its fallback `"bushy": "block/leaves_big_oak_bl"`, a texture that doesn't exist, so a leaf model that forgets `"bushy"` shows purple-and-black.
- 17 textures identical to vanilla stay (acacia, azalea, birch, cherry, jungle, mangrove, oak, pale oak and the three poplar leaves, blue orchid, oxeye daisy, red and brown mushroom, crimson and warped fungus). Vanilla 26.x ships `.png.mcmeta` mipmap settings for them, and Minecraft only reads a `.mcmeta` from the same pack as the `.png`. Removing our copies would switch vanilla's settings on and change how they look at a distance. `oxeye_daisy.png` also differs in hidden transparent-pixel colours.
- Poplar `.png.mcmeta` files (`dark_cutout`) and plain poplar models stay.
- `textures/entity/cow/red_mushroom.png` and `brown_mushroom.png` are for the mushrooms on a mooshroom's back (read by Entity Texture Features).

## README style

- Short. Sections: Flowers, Trees, Crops, Miscellaneous, then Changelog & credits. Compact two-column tables.
- Never mention OptiFine or mods the pack doesn't use. No installation or recommended-mods sections.
- Mark Continuity features with ✦ and Entity Texture Features features with ✧, each explained under the tables.
- Variant counts are distinct looks, not model files.

## Releases

1. Bump the version in `pack.mcmeta` (`§bvX.Y.Z`) and the README badge.
2. Add a `CHANGELOG.md` entry. TchicX prefers short entries.
3. Build the zip from only `pack.mcmeta`, `pack.png` and `assets`: `zip -qrX release/TchicXs_Better_Foliage_vX.Y.Z.zip pack.mcmeta pack.png assets`. `*.zip` is gitignored.
4. Check the zip contains `assets/cullleaves/options/options.json`, push to `main`, then send TchicX the zip and paste-ready release notes. Claude can't create GitHub releases or push tags (the API refuses with 403, confirmed 2026-10-04), so TchicX publishes the release.

## Verifying

- Compare textures by **pixels**, not bytes: re-saved PNGs differ in bytes but not pixels. This mistake once made vanilla textures look "new".
- For no-visual-change work, resolve every blockstate → model → parent → texture pixels (with same-pack `.mcmeta`) against vanilla 26.1, 26.2 and 26.3 before and after. Vanilla assets: `git clone --depth 1 --filter=blob:none --sparse -b <version> https://github.com/InventivetalentDev/minecraft-assets`.
- Validate every JSON file you touch.

## Background

- Many textures match fWhip's fWoliage pack. When TchicX brings a new fWhip version, compare pixel by pixel and only take what's actually different.
- **Leaf culling setup (TchicX's choice, 2026-10-04):** Cull Leaves + More Culling, with More Culling's Leaves Culling set to **Default**. More Culling stays for its other culling (signs, item frames and so on). Every leaf cube has `cullface`, so the pack also works with More Culling alone.
- **Cull Leaves**: `assets/cullleaves/options/options.json` forces `forceLeafCulling` (no faces between two leaf blocks) and `forceHideInnerLeaves` (a leaf block with leaves or solid full faces on all six sides isn't drawn at all, overhangs included), the same settings Motschen's Better Leaves ships. It only does anything when the player has Cull Leaves installed. Must stay in the release zip.
- **Why not More Culling alone:** its leaf modes only cull cube faces and never skip a whole block, so they can't remove the overhangs of buried leaves. Its closest mode (Fast) left 13% more quads and 19% more surface than Cull Leaves in an oak forest simulation (dark oak: +33% / +45%). Depth mode on top of Cull Leaves adds 1–3% (it draws leaf faces against logs that have air behind them), hence Default.
- **Compared with Better Leaves 9.6** (same simulation): this pack draws 6–13% fewer leaf quads and 1–8% less leaf surface, with or without culling mods. Averages per leaf: 9.2 quads (20% of leaves are plain cubes) vs 10.
