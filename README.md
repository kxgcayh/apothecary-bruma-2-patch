# Apothecary Bruma 2 Patch

Apothecary - Bruma Patch.esp with the records removed that Beyond Skyrim - Bruma 2.0.0 and
Beyond Skyrim - Assets SE 2026.11.11 no longer contain.

Source: Apothecary - An Alchemy Overhaul, Nexus Mods 52130, Apothecary - Bruma Patch 1.4.0.
Change: 68 INGR and MGEF override records removed (54 overriding records that Bruma 2.0.0 and Assets SE no longer contain, 14 whose effect lists named a removed effect).

A record is dangling when it overrides a `BSHeartland.esm` or `BSAssets.esm` record whose object ID is absent from the 2.0
plugins. The EditorIDs of the removed records are in neither plugin, so nothing is remapped.

## Build

    python3 build.py          # dry run, writes build/review.txt
    python3 build.py --write  # serialize with Spriggit, remove, deserialize to dist/, verify

Inputs (`inputs/`, pinned by `inputs.sha256`, not committed): the plugin from the installed mod, `BSHeartland.esm` from
Bruma 2.0.0 and `BSAssets.esm` from Assets SE 2026.11.11. Needs the Skyrim AI toolkit's `tools/spriggit-cli.sh`
(`SKYRIM_TOOLKIT` overrides its path).

## Verification

The write pass fails unless the kept FormKeys equal the output's, no output record overrides a missing record, any
dropped master is gone, and every kept record equals its input after the normalisations Spriggit makes on any round trip
(list subrecords and VMAD properties reordered, NPC_ `DNAM` padding bytes, the last bit of `QNAM` floats). Header flags
(ESL) and version are unchanged.

## Install

Copy `dist/Apothecary - Bruma Patch.esp` over the original in MO2. Reinstalling the source mod restores the original.

## Credits and Permissions

Checked on 2026-11-13 against each mod's Nexus permission block and author notes, not its description or readme. The plugin is derived from the mods below and stays under their authors' terms.

| Mod | Author | What the Nexus page says | Status |
|---|---|---|---|
| [Apothecary - An Alchemy Overhaul](https://www.nexusmods.com/skyrimspecialedition/mods/52130) | Simon Magus, DeltaRider and Oreo | Upload, modification, conversion and asset use are allowed. Author notes: no permission is needed for patches or other derivative work. | allowed |
| [Beyond Skyrim - Bruma SE](https://www.nexusmods.com/skyrimspecialedition/mods/10917) | The Beyond Skyrim - Cyrodiil Development Team | No permission block. Author notes: addons and compatibility patches may be distributed, and fixes should be shared with the team first; the full mod and resources made for Beyond Skyrim may not be redistributed. | allowed |
| [Beyond Skyrim - Assets SE](https://www.nexusmods.com/skyrimspecialedition/mods/198585) | BeyondSkyrimDC | No permission block. Author notes: as Beyond Skyrim - Bruma SE (compatibility patches allowed; the full mod and its resources may not be redistributed). | allowed |

Every source allows a patch like this with credit; credit the authors above when publishing. Beyond Skyrim asks that fixes be shared with its team first.
