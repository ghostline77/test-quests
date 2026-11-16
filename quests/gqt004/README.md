# GQT004 — Vehicle Lab

Exercise entering, riding with a contact, driving, stealing and delivering vehicles. The final stage cleans up the player vehicle and communities.

[quest.json](quest.json) owns the behavior, composition and resource inputs. Authored scenes and worlds are under `scenes/` and `world/`. The normal compiler generates all quest resources; this fixture has no custom generator, root override or copied phase template.

Build from the test-quests repository root:

```powershell
../quest-builder/target/debug/ghostline-quest-builder.exe series . --quest gqt004_vehicle_lab --out work/builds --game 'K:/Cyberpunk 2077'
../quest-builder/target/debug/ghostline-quest-builder.exe package packaging/gqt004.json --out work/packages/gqt004 --plan
```

Commands refuse an existing output destination. Refer to the [repository guide](../../README.md) for shared inputs and export ownership. Offline serialization/package verification does not replace in-game checks.
