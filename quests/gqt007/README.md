# GQT007 Barry Lipsync A/B

GQT007 is a runtime integration fixture for the localized dialogue-animation
round trip. It spawns vanilla `Character.mq010_barry`, injects Barry's vanilla
voice tag, and opens a repeatable two-option scene:

- **Play vanilla lipsync** selects `f_7D78942678897A4F`.
- **Play modified lipsync** selects `f_C39ACEAEFDC26A07`.

The two screenplay lines have distinct locstring IDs. GQT007 supplies its own
subtitle map and VO map, with both VO entries pointing to the same quest-owned
Wwise external-source conversion of Barry's vanilla **Who is it?** recording.
The matching animation names are derived from those IDs. The diagnostic modified clip forces both `jaw_mid_open` and the baked
`jaw_mid_openLipsyncPoseOutput` to `1.0`; it is intentionally exaggerated so
the result is unambiguous in game.

The scene points at a Ghostline-owned logical lipsync path. The corresponding
English localized asset is:

```text
assets/media/base/localization/en-us/lipsync/mod/gqt007/scenes/
  gqt007_barry_lipsync/civ_low_m_11_enus_40_fat.anims
```

This does not replace the vanilla Happy Together animset.

## Build

[quest.json](quest.json) owns the journal, facts, NodeRefs and resource inputs. Scene and world specs are under `scenes/` and `world/`; supplied animation and audio assets are under the repository's `assets/media/`. The compiler generates the phase graph, journal, scene, lipmap, subtitle/VO maps and registration together.

Run from the repository root:

```powershell
../quest-builder/target/debug/ghostline-quest-builder.exe series . --quest gqt007_barry_lipsync --out work/builds --game 'K:/Cyberpunk 2077'
../quest-builder/target/debug/ghostline-quest-builder.exe package packaging/gqt007.json --out work/packages/gqt007 --plan
```

The comparison animation set is a supplied native asset. Its generation belongs to the separate animation/audio tools. This quest does not recreate it or replace Barry's vanilla asset.

The test site is centred at `(-1068.2563, 1313.9362, 5.174843)`. Entering the setup trigger activates Barry, waits for readiness and starts the repeatable choice scene. In-game playback is a separate check.
