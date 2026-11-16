# GQT003 — Extract and Hold

Release Patch, escort him through three ordered destination gates and defend him against the attacker community at the final location.

[quest.json](quest.json) owns the behavior, composition and resource inputs. Authored scenes and worlds are under `scenes/` and `world/`. The normal compiler generates all quest resources; this fixture has no custom generator, root override or copied phase template.

Build from the test-quests repository root:

```powershell
../quest-builder/target/debug/ghostline-quest-builder.exe series . --quest gqt003_extract_and_hold --out work/builds --game 'K:/Cyberpunk 2077'
../quest-builder/target/debug/ghostline-quest-builder.exe package packaging/gqt003.json --out work/packages/gqt003 --plan
```

Commands refuse an existing output destination. Refer to the [repository guide](../../README.md) for shared inputs and export ownership. Offline serialization/package verification does not replace in-game checks.
