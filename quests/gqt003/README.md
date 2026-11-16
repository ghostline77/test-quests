# GQT003 — Extract and Hold

Release Patch, escort him through three ordered destination gates and defend him against the attacker community at the final location.

[quest.json](quest.json) owns the behavior, composition and resource inputs. Authored scenes and worlds are under `scenes/` and `world/`. The normal compiler generates all quest resources; this fixture has no custom generator, root override or copied phase template.

Build from the test-quests repository root:

Install the tools listed in [the authoring guide](../../docs/authoring.md) and set `GAME_ROOT` to your game installation.

```powershell
ghostline-quest-builder series . --quest gqt003_extract_and_hold --out work/builds --game $env:GAME_ROOT
ghostline-quest-builder package packaging/gqt003.json --out work/packages/gqt003 --plan
```

Commands refuse an existing output destination. Refer to the [repository guide](../../README.md) for shared inputs and export ownership. Offline serialization/package verification does not replace in-game checks.
