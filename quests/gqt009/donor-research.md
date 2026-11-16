# Cross-platform replacement donor audit

For the subsequent 492-file audit and proposed cross-series slot allocations, see [the shared character slot inventory](../../research/modio-character-slots/README.md). It identifies 24 statically audited candidate pairs (11 base-game-only, 13 additional with Phantom Liberty), with runtime validation still outstanding.

Audited the installed game on 2026-11-08. No game files were changed and nothing was installed.

## Recommended base-game candidate

- Root: `base\characters\entities\to_be_removed\_e3_trailer_mb.ent`
- Appearance replacement slot: `base\characters\appearances\quest_temp\woman_fat.app`

Both resources exist and decode successfully. The root contains a `gamePuppet`, compiled components and 25 appearance mappings. Neither base-game nor expansion TweakDB has an `entityTemplatePath` pointing to this root. No inbound imports to either candidate were found in the scanned resources.

The E3 root's original `_e3_trailer_mb.app` does not exist in the installed archives, so it cannot itself be used as an existing replacement target. The proposed appearance slot is an independent existing file. Its filename does not select the skeleton: a replacement would supply the intended male_big components and rig and update the replaced root's mapping accordingly. Its existing definitions are `default`, `sq011_denny_rich`, `sq021_joss` and `q001_epilog_house_woman`; these names alone do not establish current usage, and no imports to this resource were found. Preserve the original root appearance mapping names required by the replacement contract.

An alternative appearance slot is `ep1\characters\appearances\citizen\test\black_sapphire\black_sapphire_mb.app`. It also exists, decodes and has no imports in the scan, but would require Phantom Liberty availability. Prefer the base-game pair for a base-game encounter candidate.

## Rejected or less suitable donors

- `entities\to_be_removed\animals_gang_mb.ent`: three distinct character records still point to it, present in both caches.
- `appearances\gang\gang__animals_mb.app` and `gang__animals_mba.app`: shared by multiple roots.
- `appearances\to_be_removed\asian_ma.app` and `asian_vendor_ma.app`: referenced by shipped quest/gig roots despite the directory name.
- E3 trailer appearance paths: absent from the installed archives.
- `main_npc\animal_boss\test.ent`: no imports or character records found, but it is a small `entEntity` mesh assembly rather than a full NPC puppet.

## Evidence and limits

The read-only `ghostline-red` example `donor-audit` scanned 57 vanilla content/expansion/hotfix archives, 590,027 archive entries and 833,297 archive dependency entries. It inspected native CR2W import tables for 91,373 known-path entity, appearance, quest, questphase, scene, streaming sector/block, community and CSV resources, with zero inspection errors. Positive controls found Judy's appearance references and the mantis weapon mesh import. Archive dependency tables alone were insufficient and were not treated as proof of isolation.

Both `r6/cache/tweakdb.bin` and `tweakdb_ep1.bin` were checked for exact `entityTemplatePath` references. The scan excludes mods, unknown-path payloads, scripts, runtime-generated resource references and non-import references in opaque data. This is a strong static candidate, not proof of zero runtime side effects or console acceptance. A replacement package still needs native readback, mod.io compatibility validation and an explicitly authorized runtime test.

Detailed machine-readable results and native decoded samples are in `work/donor-audit/`, including `report.json`. These are reproducible scratch evidence, not shipping assets.
