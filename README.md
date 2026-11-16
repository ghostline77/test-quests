# Quest tests

Independent authored fixtures for the standalone quest builder. Included quests are GQT001, GQT002, GQT003, GQT004, GQT006, GQT007, GQT008 and GQT009. Specialist race and advanced braindance fixtures are maintained separately.

Every fixture lives under `quests/<id>/` and has a `quest.json` compiler entry point. Scene/world specs are under `scenes/` and `world/`; dialogue and character authoring stay with their owning fixture. Shared published media lives under `assets/media/`.

`series.json` lists the fixtures. `project.json` declares owned depot prefixes and the explicit Ghostline dependency used by Patch fixtures. `packaging/<id>.json` selects a native build. Generated outputs and local evidence belong in ignored `work/`.

## Build and edit

Use [the fixture guide](docs/authoring.md) to build one test, inspect its package
and prepare an in-game check.

GQT008's lab is generated from its building project by the standalone building builder:

```powershell
../building-builder/target/release/ghostline-building-builder.exe export quests/gqt008/world/interaction-lab.building.json --game 'path/to/Cyberpunk 2077' --out work/buildings/interaction-lab
../quest-builder/target/release/ghostline-quest-builder.exe series . --out work/builds --game 'path/to/Cyberpunk 2077'
../quest-builder/target/release/ghostline-quest-builder.exe package packaging/gqt008.json --out work/packages/gqt008 --plan
```

Run from this repository. Commands refuse existing output destinations. The quest resource inputs pin published native building outputs by hash. GQT007 consumes supplied voice/lipsync assets; audio generation is separate.

Native build/readback and package verification are offline checks. They do not replace game checks of scene progression, combat, streaming, navigation or save/load.
