# Gameplay and SRAM validation

## ChaosRush Edition v1.0: completed-game report

**Report received:** October 20, 2026

**Edition:** TopCat's FFI+II ChaosRush Edition, integrating Chaos Rush's FF1 v1.3 and FF2 v2.2b translations with Grond's menu and the dual-save/NPC fixes.

**Maintainer gameplay report:** Both Final Fantasy I and Final Fantasy II were played to completion in this compilation; both endings were viewed. The maintainer reports no errors during those playthroughs and supplied a single 32 KiB battery-save (`.srm`) preserving progress in both games. The emulator or hardware platform has not been established in this report.

This is **maintainer-reported full-playthrough testing**, not an independent emulator replay or proof of compatibility with all software and hardware.

## Inspection of the supplied battery save

The supplied `.srm` is **32,768 bytes (32 KiB)**, consistent with the original compilation's SXROM board and four 8 KiB PRG-RAM banks. An inspection of the actual bytes found:

| File offset range | Observed state | Interpretation |
| --- | --- | --- |
| `0x0000–0x1FFF` | 5,688 nonzero bytes | Populated data consistent with FF1 save/work RAM |
| `0x2000–0x3FFF` | All zero | Unused bank in this snapshot |
| `0x4000–0x5FFF` | All zero | Unused bank in this snapshot |
| `0x6000–0x7FFF` | 6,777 nonzero bytes | Populated data consistent with FF2 save/work RAM |

Additional structure within the FFII-associated bank supports the identification: five distinct 768-byte (`0x300`) record positions begin at `0x6000`, `0x6300`, `0x6600`, `0x6900` and `0x6C00`. This spacing matches the documented NES FFII save layout (one working slot plus four numbered slots). The 768-byte records at `0x6000` and `0x6C00` are **byte-identical** in the supplied snapshot. See the [FFII SRAM layout reference](https://datacrystal.tcrf.net/wiki/Final_Fantasy_II/RAM_map) and the [SXROM board profile](https://nescartdb.com/profile/view/3950/final-fantasy-i-ii).

### What this does and does not demonstrate

The file contains simultaneously populated, nonoverlapping bank regions consistent with both FF1 and FF2. Together with the maintainer's report of completing both games, it provides strong practical support for the dual-save restoration in this tested edition.

This static snapshot **cannot on its own prove** that both endings were viewed, that every story flag or game-save checksum is correct, that loading was retested after each completion, or that no failures could occur on other emulators or real cartridges. Those distinctions should be kept explicit.

### Save-file privacy

The `.srm` was used for inspection only and **has not been uploaded to this public repository**. No character names, raw save contents, or personal-save hashes are published here. Redistribution of the save requires separate approval from its owner.

## Other editions

The **Save and NPCFix** and **USA Prototype** editions have distinct translation and menu combinations. This successful ChaosRush Edition report does not independently validate complete playthroughs for those two versions.

## Further testing

For repeatable compatibility reports, record the emulator and version or cartridge hardware, confirm a cold boot into the selector, save and reload both games independently, and document the selected save slots. For hardware validation, include the cartridge board/flashcart and save retention across power cycling.
