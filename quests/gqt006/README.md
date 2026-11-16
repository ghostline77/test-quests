# GQT006 — Cyberpsycho encounter

Regina's authored messages, Goth Baddie's challenge and combat outcomes share the quest composition. The scene/world specs define the encounter, aftermath and readable evidence; the character project owns the authored appearances and combat loadout.

[quest.json](quest.json) owns the behavior, composition and resource inputs. Authored scenes and worlds are under `scenes/` and `world/`. The normal compiler generates all quest resources; this fixture has no custom generator, root override or copied phase template.

Build from the test-quests repository root:

```powershell
../quest-builder/target/debug/ghostline-quest-builder.exe series . --quest gqt006_goth_baddie_cyberpsycho --out work/builds --game 'K:/Cyberpunk 2077'
../quest-builder/target/debug/ghostline-quest-builder.exe package packaging/gqt006.json --out work/packages/gqt006 --plan
```

Commands refuse an existing output destination. Refer to the [repository guide](../../README.md) for shared inputs and export ownership. Offline serialization/package verification does not replace in-game checks.
