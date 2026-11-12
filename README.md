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

Credit goes to the authors of the mods below. Permission status is based on each mod's Nexus page permissions, read on 2026-11-13.

- [Apothecary - An Alchemy Overhaul](https://www.nexusmods.com/skyrimspecialedition/mods/52130) by Simon Magus, DeltaRider and Oreo: allowed based on the Nexus page permissions
- [Beyond Skyrim - Bruma SE](https://www.nexusmods.com/skyrimspecialedition/mods/10917) by The Beyond Skyrim - Cyrodiil Development Team: allowed based on the Nexus page permissions
- [Beyond Skyrim - Assets SE](https://www.nexusmods.com/skyrimspecialedition/mods/198585) by BeyondSkyrimDC: allowed based on the Nexus page permissions

Credit the authors above and share fixes with the Beyond Skyrim team.

