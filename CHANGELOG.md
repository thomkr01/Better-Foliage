# Changelog

All notable changes to TchicX's Better Foliage. This project uses [semantic versioning](https://semver.org/).

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
