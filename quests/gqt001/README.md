# GQT001 — Signal Delay

Read a quest-owned terminal document, wait for the scheduled reply and complete Patch's ordered confirmation conversation.

[quest.json](quest.json) owns the behavior, composition and resource inputs. Authored scenes and worlds are under `scenes/` and `world/`. The normal compiler generates all quest resources; this fixture has no custom generator, root override or copied phase template.

Build from the test-quests repository root:

```powershell
../quest-builder/target/debug/ghostline-quest-builder.exe series . --quest gqt001_signal_delay --out work/builds --game 'K:/Cyberpunk 2077'
../quest-builder/target/debug/ghostline-quest-builder.exe package packaging/gqt001.json --out work/packages/gqt001 --plan
```

Commands refuse an existing output destination. Refer to the [repository guide](../../README.md) for shared inputs and export ownership. Offline serialization/package verification does not replace in-game checks.
