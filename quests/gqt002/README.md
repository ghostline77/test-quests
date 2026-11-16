# GQT002 — Quiet Install

Activate the guarded site, acquire and plant the item while monitoring the optional stealth condition, then retire the guards and complete the quest.

[quest.json](quest.json) owns the behavior, composition and resource inputs. Authored scenes and worlds are under `scenes/` and `world/`. The normal compiler generates all quest resources; this fixture has no custom generator, root override or copied phase template.

Build from the test-quests repository root:

```powershell
../quest-builder/target/debug/ghostline-quest-builder.exe series . --quest gqt002_quiet_install --out work/builds --game 'K:/Cyberpunk 2077'
../quest-builder/target/debug/ghostline-quest-builder.exe package packaging/gqt002.json --out work/packages/gqt002 --plan
```

Commands refuse an existing output destination. Refer to the [repository guide](../../README.md) for shared inputs and export ownership. Offline serialization/package verification does not replace in-game checks.
