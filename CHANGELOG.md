# Changelog

All notable changes to TchicX's Better Foliage. This project uses [semantic versioning](https://semver.org/).

## [6.1.1] – 2026-09-28

Nothing changes in-game. The pack was checked block by block against Minecraft 26.1, 26.2 and 26.3.

### Changed
- Removed 99 files that were identical to Minecraft's own.
- Merged duplicate leaf models and textures into one copy each.
- Gave every JSON file the same layout.
- Losslessly compressed all images, making them about 32% smaller.

### Fixed
- The 6.1.0 notes listed new Tall Grass and Vine textures, but they were identical to vanilla, so they've been removed.
- README variant counts for Acacia, Cherry, Azalea and Flowering Azalea leaves: 3 each, not 5.

## [6.1.0] – 2026-09-28

### Added
- Bushy leaves for Orange, Yellow and Red Poplar leaves (Minecraft 26.3).
- Short Grass is back, with 3 random variants.
- New textures for Tall Grass and Vines.
- Mooshrooms show the pack's mushroom textures on their backs (needs Entity Texture Features).

### Changed
- Updated for Minecraft 26.1 – 26.3 (pack format 84–97.1).

## [6.0.2] – 2026-09-27

### Changed
- Moss Carpet renders faster: removed 256 invisible faces (on zero-thickness blades) from its main model, cutting it from 414 to 158 faces. It looks the same.
- Tidied the leaf blockstates: each tree now has a single variant list instead of the same list repeated for every leaf distance. Oak keeps its own list for leaves next to logs, which are slightly less bushy on purpose. No visual change.
- Every model and blockstate file now carries a "Made by TchicX for TchicX's Better Foliage" credit label (replacing the old "Made with Blockbench" ones). The OptiFine/Continuity properties files have it as a comment.

## [6.0.1] – 2026-09-23

Optimized for culling: every leaf model now supports face culling, so the pack works with culling mods like More Culling.

### Fixed
- Plain (non-bushy) leaf blocks can now be culled. Their faces were missing `cullface`, so they always drew all six sides, even next to other leaves, logs or solid blocks and with culling mods. They look the same, but dense forests render faster.

## [6.0.0] – 2026-09-23

A focused rework: the pack now covers plant life only.

### Changed
- The pack now covers flowers, crops, bushes, leaves, flower pots, mushrooms and nether plants, glow lichen and moss carpet.
- Updated for Minecraft 26.1 – 26.2 (pack format 84–88).
- New pack menu description: "Varied plant life!"

### Fixed
- Peony now uses all six of its lower-half variants (one slot repeated variant 2).
- Lilac, Peony and Rose Bush blockstates had an extra closing bracket that could stop them from loading.
- Potted plants no longer look darker than the same plant outside a pot.

### Removed
- Grass and ferns, cactus, lily pads and vines.
- Grass block, dirt path, podzol, mycelium and nylium textures.
- Bee nests and beehives, campfires, fire, water, rain and snow, iron bars and trapdoors.
- Custom sounds, fonts, subtitles, entity textures and tool/food item models.
- Unused and outdated files left over from older versions.

## [5.3.0]
- Previous release (grass, shadows and more).
