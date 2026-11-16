# GQT004 — Vehicle Lab

Exercise entering, riding with a contact, driving, stealing and delivering vehicles. The final stage cleans up the player vehicle and communities.

[quest.json](quest.json) owns the behavior, composition and resource inputs. Authored scenes and worlds are under `scenes/` and `world/`. The normal compiler generates all quest resources; this fixture has no custom generator, root override or copied phase template.

Build from the test-quests repository root:

Install the tools listed in [the authoring guide](../../docs/authoring.md) and set `GAME_ROOT` to your game installation.

```powershell
ghostline-quest-builder series . --quest gqt004_vehicle_lab --out work/builds --game $env:GAME_ROOT
ghostline-quest-builder package packaging/gqt004.json --out work/packages/gqt004 --plan
```

Commands refuse an existing output destination. Refer to the [repository guide](../../README.md) for shared inputs and export ownership. Offline serialization/package verification does not replace in-game checks.
