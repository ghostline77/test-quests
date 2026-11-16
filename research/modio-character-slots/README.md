# Character replacement slot inventory

The 2026-11-08 static audit of the previously identified 492 candidates leaves **24 disjoint root/appearance pairs**: **11 base-game-only allocations plus 13 additional allocations requiring Phantom Liberty**. See [inventory.json](inventory.json) for exact paths, original appearance names, source fingerprints, exclusions and allocation ownership.

This is an audited candidate pool, not a runtime-certified or global maximum. No replacement was installed or uploaded to mod.io. The original 492 count described files selected from character entity/appearance directories; it was not a count of complete characters or free slots.

## What was checked

- 57 vanilla content, expansion and hotfix archives.
- 467,432 resource metadata payloads and structural buffers, including unknown-path entries: 37,275,435,760 decoded bytes. Audio/video payload families and external pixel/geometry buffers were excluded.
- Native import tables and archive dependency tables, with literal path, slash-variant, UTF-16 and binary 64-bit resource-hash searches.
- Both compiled TweakDB caches, checking resource-reference flats as well as character entity-template bindings.
- All 135 known native CSV tables: 7,733 decoded rows, including the factory registry and its child tables. Six empty tables were independently checked against their native appendix bytes. None referenced these 492 candidates.
- Both installed compiled script bundles, loose scripts/configuration and the game executable. The compiled bundles' v14 string/name/resource table bounds were checked separately; their resource pools contain 79 and 96 entries. Name-only script/executable matches remain excluded.
- Native serialization of all 492 candidates to verify actual resource types, compiled NPC roots and original appearance mappings. All 627 candidate/table serialization jobs completed without failure.
- Installed archive/REDmod replacements for collisions with the selected paths; none of the 24 pairs is currently overridden.
- A positive control using an actual native mantis entity confirmed that the reference matcher detects its rig dependency. The earlier import-table audit separately found known Judy appearance and mantis mesh dependencies.

The raw scan reported zero read/decode errors. The supplemental native documents are authoritative for root types and table rows: the low-level in-memory decoder used by the raw scanner can retain opaque table appendices and unexpanded compiled packages.

## Why 492 became 24 pairs

| Classification | Files |
| --- | ---: |
| Player/corpse resource families withheld for unresolved runtime selection | 245 |
| Other files not validated as complete NPC roots or usable appearance resources | 128 |
| Unresolved script/executable name matches | 28 |
| Valid resources with no known references after the static checks | 91 |
| **Total audited** | **492** |

The 91 remaining resources comprise 67 NPC roots and 24 appearance resources. There are 50 base-game roots and 17 expansion roots; appearance resources are the limiting factor, with 11 base-game files and 13 expansion files.

Corpse files were not cleared merely because their complete paths did not appear literally. Their family/body naming and the engine's appearance-selection machinery leave dynamic selection unresolved. They are withheld, not asserted to be individually proven active. The same conservative rule applies to player resource families. Files rejected by the NPC-root check may still be usable with a different replacement strategy; they are not counted here.

## Sharing the pool across quest mods

`GLCHAR0001` through `GLCHAR0024` are proposed allocations. Each owns a different `.ent` path and a different `.app` path. Original bodies or filename genders do not constrain replacement contents when both files are replaced coherently, but native naming contracts must be preserved.

1. Reserve an entire pair for one owning quest mod/series before shipping it; set its `owner` explicitly. All owners currently remain null.
2. Another independently distributed mod must use a different pair. Different definition names inside the same replaced `.app` do not prevent archive conflicts.
3. A mod may be able to hold multiple compatible character appearances in its own pair. Therefore 24 pairs is not necessarily a 24-NPC limit. Shared root rig/behavior contracts and preserved native appearance names still apply.
4. Continue referencing shared vanilla meshes, textures and rigs without modifying them. Any additional mesh, rig or material replacement needs its own reserved paths; those are not included in this pair count.
5. Keep record IDs, facts and other mod-owned identifiers distinct as well. Donor reservation only prevents resource-path collisions.
6. Pin the allocated inventory. The generator refuses to overwrite a file containing non-null owners; do not renumber existing allocations during a game-patch audit.

The first pair actually used must still be validated as a replacement in the game and on the target mod.io platform. This audit establishes a conservative static allocation pool; it cannot prove the absence of every dynamically constructed native-code lookup or conflicts with arbitrary third-party mods installed later.

## Evidence and reproduction

Detailed scratch evidence is in `work/donor-audit/`: `deep-report.json`, `decode-all-report.json`, `decoded/`, `script-pools.json` and `game-fingerprint.json`. The source inventory contains the selected donor archive entry SHA-1s so an audit can detect changed source resources after a patch.

The native Rust audit tools are in `ghostline-red/examples/`:

- `donor-audit`: archive imports, dependency tables and TweakDB resource references.
- `donor-deep-audit`: literal/hash scans across metadata, structural buffers, scripts and native code.
- `donor-slot-inventory`: native-document/table validation, conservative exclusions, disjoint pairing, source fingerprints and installed-mod collision checks.

All outputs were created outside the game directory. Nothing was installed and no game files were modified.
