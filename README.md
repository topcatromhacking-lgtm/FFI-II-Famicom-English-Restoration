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
| **Save and NPCFix** | The original Neo Demiforce English compilation, with the NPC-freeze/save restoration approach and the corrected multicart presentation. Best for preserving the classic fan-translation experience. | Neo Demiforce; Grond; TopCat integration | [Romhacking.net #7555](https://www.romhacking.net/translations/7555/) |
| **The Prototype Edition** | The **North American Final Fantasy** and the surviving **unreleased US Final Fantasy II prototype** together in the original compilation format. Best for experiencing the historically unfinished US localization. | Square's original localizations; Lost Levels' preservation of the FFII prototype; Grond; TopCat integration | [Romhacking.net #7556](https://www.romhacking.net/translations/7556/) |
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

**Only IPS delta patches belong in this public repository. There are no game ROMs, copyrighted game-image dumps, saved games, tools, or build scripts.**

The three historical releases and their downloads can currently be found at the original publication pages:

- [Save and NPCFix, release #7555](https://www.romhacking.net/translations/7555/)
- [The Prototype Edition, release #7556](https://www.romhacking.net/translations/7556/)
- [ChaosRush Edition, release #7557](https://www.romhacking.net/translations/7557/)

**Repository mirror status:** the original three IPS files have **not yet been reverified and mirrored into this GitHub repository**. The original release pages are the available distribution references until verified IPS files are added. We will not recreate the bytes of a missing patch from its description, and no new ROM builds are included here.

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

This README **does not assert** that every complete playthrough, real-hardware configuration, emulator, or combination of save states has been tested. Please report the exact edition, emulator/hardware, NPC/location, sequence of steps and the result, without publishing ROMs or personal save data.

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

**Do not upload or link complete prepatched ROM images here.** Please preserve the original translators' credits when sharing these patches or describing the work.
