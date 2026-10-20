# Final Fantasy I+II — Famicom English Restoration

An unofficial restoration of **Final Fantasy I+II** (1994, Famicom/NES compilation), prepared by **TopCat**. The project documents and preserves three English-edition patches of the original two-game cartridge, with particular attention to the game-selection menu, boot behavior, Final Fantasy I NPC freezes, and game-save handling.

**This is the original 8-bit Famicom compilation, not Final Fantasy Origins, Dawn of Souls, or the WonderSwan Color games.**

## Why the restoration was needed

Square's Japanese-only `Final Fantasy I+II` compilation includes both games under one cartridge and a common game-selection menu. The earlier English compilation work by **Neo Demiforce** made the two-game experience accessible in English, but the combined ROM had significant technical limitations. Most notably, interacting with NPCs in **Final Fantasy I** could freeze the game, and the original save handling could cause the two games to interfere with each other's progress.

**Grond** developed an addendum addressing the well-known freeze and save issues, together with changes to the multicart menu. Building on that history, this project prepared three distinct English alternatives: a corrected Demiforce edition, an edition using the unreleased North American FFII prototype, and an edition integrating the more recent Chaos Rush translations.

These are **three alternatives**, not three patches that must be applied one after another.

## The three editions

| Edition | What you get | Translation and source credits | Historical release |
| --- | --- | --- | --- |
| **Save and NPCFix** | The original Neo Demiforce English compilation with NPC-freeze and dual-save repairs, while retaining the original compilation's selection screen (not Grond's redesigned screen or dash). Best for preserving the classic fan-translation experience. | Neo Demiforce; Grond; TopCat integration | [Romhacking.net #7555](https://www.romhacking.net/translations/7555/) |
| **The Prototype Edition** | The **North American Final Fantasy** and the surviving **unreleased US Final Fantasy II prototype** together in the original compilation format, using its original selector (without Grond's custom menu or dash). Best for experiencing the historically unfinished US localization. | Square's original localizations; Lost Levels' preservation of the FFII prototype; Grond; TopCat integration | [Romhacking.net #7556](https://www.romhacking.net/translations/7556/) |
| **ChaosRush Edition** | The combined game with **Chaos Rush's Final Fantasy v1.3** and **Final Fantasy II v2.2b** English translations, providing terminology and scripts closer to later official localization conventions. | Chaos Rush and his collaborators; Grond; TopCat integration | [Romhacking.net #7557](https://www.romhacking.net/translations/7557/) |

The project versions are based on the three **TopCat v1.0 releases dated October 26, 2025**. Each edition has its own translation lineage. No claim is made that the original translation scripts were authored by TopCat.

## The technical restoration

### 1. Preserve the multicart boot and selector

Combining newer single-game translation builds into the compilation is not equivalent to concatenating the two ROMs. The multicart has its own boot/setup code and banking assumptions. During development of the merged build, we traced an apparent direct-boot/menu failure to a missing or zero-filled **512-byte ROM block at file offsets `0x3FE00–0x3FFFF`**. Restoring this block from the working Grond-based compilation restored the selector in the tested build.

This is a **confirmed project-specific repair of the merged menu path**, not proof that every NPC freeze or save issue originates in those 512 bytes. These are distinct issues.

### 2. Address the Final Fantasy I NPC freeze

The older English compilation was known to freeze when talking to certain NPCs in **Final Fantasy I**. The Grond addendum addresses this problem; the corrected edition incorporates that established work. This project aims to retain the repair when using alternative English game data.

### 3. Respect the two games' save memory

The combined cartridge requires correct save-memory handling for two games. Earlier builds could share or overwrite save data across titles. Grond's changes addressed that limitation. The restored editions preserve the intended dual-game architecture rather than treating each title as an unrelated standalone ROM.

The **NES 2.0 header** details matter for emulator and save-RAM detection. Support still depends on emulator/cartridge implementation. Back up existing saves before testing different editions.

### 4. Keep translation and boot changes separate

The **ChaosRush Edition** uses the standalone English text/data of Final Fantasy v1.3 and Final Fantasy II v2.2b, while retaining the multicart's essential boot and selection components. The original user-confirmed missing-block issue illustrates why translating a standalone game and integrating it into the multicart are different technical tasks.

The **Prototype Edition** is deliberately distinct: it preserves the historical US-prototype character rather than presenting a completed modern FFII translation.

## Patches and installation

**This public repository now preserves all three original TopCat v1.0 IPS patches, their SHA-256 verification manifest, and one explicitly authorized completed-game SRAM save. No complete game ROMs, copyrighted game-image dumps, tools, or build scripts are included.**

### Download the original IPS patches (GitHub)

| Edition | Download IPS | Historical publication |
| --- | --- | --- |
| **Save and NPCFix** (Demiforce) | [Original .ips](patches/Final%20Fantasy%20I%20%26%20II%20%28J%29%20%5BT%2BDemiforce_v1.0%5D%2BSaveNPCFix-TopCat.ips) | [Romhacking.net #7555](https://www.romhacking.net/translations/7555/) |
| **USA Prototype Edition** | [Original .ips](patches/Final%20Fantasy%20I%20%26%20II%20USA%20Prototype%20Edition%2BFix-TopCat.ips) | [Romhacking.net #7556](https://www.romhacking.net/translations/7556/) |
| **ChaosRush Edition** (includes Grond menu) | [Original .ips](patches/Final%20Fantasy%20I%20%26%20II%20%5BChaosRush1.3-2.2b%2BMenu-Grond%2BSaveNPCFix-TopCat.ips) | [Romhacking.net #7557](https://www.romhacking.net/translations/7557/) |

**Integrity and preservation:** [patches/SHA256SUMS.txt](patches/SHA256SUMS.txt) contains the original SHA-256 checksums. On October 20, 2026, all three repository files were verified **byte for byte** against the owner-supplied archival ZIP by comparing their Git blob SHA-1 identifiers, in addition to their recorded sizes and SHA-256 values. See [PATCH-VERIFICATION.md](PATCH-VERIFICATION.md) and the [patch archive's versioning policy](patches/README.md). The original patches remain unchanged; any future improvements should be distributed as separately versioned patches.

Structural verification is not a substitute for gameplay testing, and the files have not been independently matched against downloads from Romhacking.net. This repository distributes **IPS patches, not ROM images**.

### Base ROM identity

The documented source is the **unmodified Japanese `Final Fantasy I & II (J) [!].nes`** image, including its normal 16-byte NES header:

| Property | Expected value |
| --- | --- |
| Platform | Nintendo Famicom / NES |
| PRG-ROM | 512 KiB |
| Mapper/board | MMC1 / HVC-SXROM |
| CRC32, complete source file | `6F8906AD` |
| MD5, complete source file | `6CDB7B50C897956A9B32E5AA27A37216` |
| SHA-1, complete source file | `4B22C2C88FC71EACF270EA51EF218944BB4C536A` |
| SHA-256, complete source file | `7F9E40ADA806156D250803CEC9CC6F063E378028A561E0FDA018271A578FDD59` |

These values identify the original reference dump, **not** the hashes of the three finished editions. Verify the specific IPS distribution's accompanying readme, patch direction, and input requirements before applying it. Do not mix headered and headerless inputs.

1. Make a backup of your own, legally obtained original Japanese multicart dump and existing saves.
2. Choose **exactly one** of the three editions; the alternatives are not cumulative.
3. Check the original ROM's checksum against the reference above.
4. Apply your chosen edition's verified `.ips` patch with any IPS-compatible patcher to a **new output file**, following the original release's instructions.
5. Boot the output and test the game-selection menu, launch **both** games, talk to FF1 NPCs, and verify independent saving/reloading in both titles.

Don't apply a standalone FF1 or FFII English translation patch over an already assembled compilation unless its instructions explicitly say to do so.

## Status and testing

The historical development established the cause of a merged-build selector failure and verified that restoring the missing multicart block made the menu appear again. The original release descriptions document the three editions and the restoration goals.

**ChaosRush Edition:** As reported on October 20, 2026, the maintainer completed **both FF1 and FF2**, saw both endings, and encountered no errors in the playthroughs. A supplied 32 KiB battery save was privately inspected and contains data in two distinct 8 KiB banks consistent with both games' save arrangements. The FFII-associated region exhibits the documented 768-byte slot spacing. Details and limits are recorded in [GAMEPLAY-VALIDATION.md](GAMEPLAY-VALIDATION.md). **The original 32 KiB save is now [publicly available with its owner's permission](saves/Final%20Fantasy%20I%20%26%20II%20%5BChaosRush1.3%2B2.2b%2BMenuByGrond%2BSaveFixbyTopCat%5D.srm)**, with its SHA-256 checksum, usage notes and limitations documented in [GAMEPLAY-VALIDATION.md](GAMEPLAY-VALIDATION.md).

This is maintainer-reported playthrough evidence supported by structural save-file inspection, not independent reproduction of the endings. It does **not** establish that every real-hardware configuration, emulator, or combination of save states has been tested, or that the other two editions have also been completed. Please report the exact edition, emulator/hardware, NPC/location, sequence of steps and the result, without publishing ROMs or other people's saves without their consent.

## Credits and provenance

- **Square (now Square Enix)**: original Final Fantasy I, Final Fantasy II, and Final Fantasy I+II games; official North American FF1 localization and historical FFII prototype.
- **Neo Demiforce / Demi**: pioneering English translations and early compilation work.
- **Grond**: multicart title/menu work and the freeze/save addendum underpinning the restoration.
- **Chaos Rush**, with his credited collaborators: the newer FF1 and FFII English translations used in the ChaosRush Edition.
- **Lost Levels**: preservation and documentation of the unreleased North American FFII prototype.
- **TopCat**: integration, debugging, multicart menu restoration, variant preparation and documentation.

Historical references:
- [Demiforce/Grond English compilation addendum](https://www.romhacking.net/translations/3366/)
- [Save and NPCFix](https://www.romhacking.net/translations/7555/)
- [The Prototype Edition](https://www.romhacking.net/translations/7556/)
- [ChaosRush Edition](https://www.romhacking.net/translations/7557/)
- [Chaos Rush's standalone FF1](https://www.romhacking.net/translations/4868/) and [FFII](https://www.romhacking.net/translations/2656/)

## Distribution

This is an unofficial, free, noncommercial fan restoration, unaffiliated with Square Enix, Nintendo or the original translation groups. All game names, characters, art, and code belong to their respective rights holders.

**Do not upload or link complete prepatched ROM images here.** The publicly shared ChaosRush SRAM save is a specifically authorized test artifact, not a ROM or game image. Please preserve the original translators' credits when sharing these patches or describing the work.
