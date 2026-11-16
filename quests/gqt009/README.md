# GQT009 — Cyberpsycho Sighting: Heavy Metal

A standalone Cyberpsycho encounter in Kabuki starring Darius "Shears" Voss, a
`male_big` NPC wearing native big-body clothing and fitted NPC mantis blades.
Regina supplies a text briefing, an evidence shard and an outcome-sensitive
debrief. The encounter supports lethal and nonlethal resolution.

The world uses GQT006's origin at `(-1026.8678, 1279.5898, 5.1301804)`.
It owns its quest, community, weapon, character, journal and localization under
`mod/gqt009`. No GQT006 scenes, character resources, audio or follow-up content
are included. Test these encounters separately because they share the site.

## Build and package

Run from the `test-quests` repository root. The native character and mechanical
fit are generated from the authored character project; clothing refitting stays
disabled. Commands below use the normal executable locations and publish into
`work/`. Export/build output destinations must be absent before a fresh build.

```powershell
../character-builder/target/release/ghostline-character-builder.exe build quests/gqt009/characters/heavy_metal.character.json --catalogue ../items/dist/catalogue --game 'K:/Cyberpunk 2077' --export --out work/characters/heavy_metal
../character-builder/target/release/ghostline-character-builder.exe review-cyberware --project quests/gqt009/characters/heavy_metal.character.json --catalogue ../items/dist/catalogue --game 'K:/Cyberpunk 2077' --template male_big --entity 'base\characters\cyberware\npc\psycho_mantisblade.ent' --fit --depot 'mod\gqt009\cyberware' --out work/cyberware/heavy_metal
../ghostline-red/target/release/ghostline-red.exe cr2w-deserialize quests/gqt009/weapons/factory.csv.json work/cyberware/heavy_metal/factory.csv
../quest-builder/target/release/ghostline-quest-builder.exe compile quests/gqt009/quest.json --out work/builds/gqt009_heavy_metal --game 'K:/Cyberpunk 2077'
../quest-builder/target/release/ghostline-quest-builder.exe scenarios quests/gqt009/quest.json quests/gqt009/scenarios.json --out work/gqt009-scenarios.json
../quest-builder/target/release/ghostline-quest-builder.exe package packaging/gqt009.json --out work/packages/gqt009
```

The published character archive supplies appearance resources. The quest's
TweakXL owns the sole runtime character definition, native mantis combat base,
boss tuning and equipment group. The fitted weapon keeps the native NPC mantis
equip/unequip conditions through the corresponding native equipment-item base.
Its own compiled factory selects the fitted entity; no base-game weapon is
replaced.

The ZIP requires RED4ext, ArchiveXL and TweakXL. Native resource/dependency and
package readback checks are offline evidence. Gameplay, big-rig combat animation,
navigation, difficulty and real game save/load remain pending until installation
is authorized. Nothing is installed by the build or package commands.

See [WALKTHROUGH.md](WALKTHROUGH.md) for the player route and pending playtest.

## Current package

`work/packages/gqt009/Ghostline_GQT009_HeavyMetal.zip` contains the standalone
archive, merged ArchiveXL registration and Cyberpsycho TweakXL. Native build
readback, both structural routing scenarios, archive extraction and ZIP byte
verification passed. The package contains 22 GQT009-owned native resources and
no scene resources or GQT006 assets. It has not been installed or playtested.
