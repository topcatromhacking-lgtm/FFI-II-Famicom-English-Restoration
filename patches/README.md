# Original IPS patches

This directory is intended to contain the **three original TopCat v1.0 IPS files** for the Famicom/NES *Final Fantasy I+II* compilation, as published on Romhacking.net on October 26, 2025. These are **alternative, independent patches** for the original Japanese Famicom compilation, **not incremental patches** to apply in sequence.

## Files to preserve

| Edition | Original IPS filename | Bytes | SHA-256 |
| --- | --- | ---: | --- |
| Save and NPCFix | `Final Fantasy I & II (J) [T+Demiforce_v1.0]+SaveNPCFix-TopCat.ips` | 90,743 | `bafa0d7ab67525d0b77469b3c1227566ab21ff676dc331203056a8f5c2fff102` |
| US Prototype Edition | `Final Fantasy I & II USA Prototype Edition+Fix-TopCat.ips` | 127,123 | `27b194b0cafcc7e3d9e46cff4bbabcffc825eaabf5aac73f3627b6ed1e93d44f` |
| ChaosRush Edition | `Final Fantasy I & II [ChaosRush1.3-2.2b+Menu-Grond+SaveNPCFix-TopCat.ips` | 69,701 | `40961c1851926017279c8a8f94daa6c581e1576d69b50cada5318ce11fa01fbe` |

**Current status:** The original IPS files are verified against the owner's archival ZIP but are **not yet present in this directory**. They will be published here without modifying the original bytes.

The owner-supplied archive passed ZIP integrity checks. Each IPS parsed completely with valid `PATCH` and `EOF` markers and no overlapping records. These are structural validations, not a guarantee of compatibility with all emulators or hardware. For full technical details see [PATCH-VERIFICATION.md](../PATCH-VERIFICATION.md).

The maintainer additionally reports completing both FF1 and FF2 through their endings without errors in the **ChaosRush Edition**, and shared an [authorized SRAM completion save](../GAMEPLAY-VALIDATION.md). The other two editions do not inherit that same level of playthrough testing.

## Installation

1. Obtain your own lawful, unmodified Japanese *Final Fantasy I & II (J) [!].nes* dump and back it up. SHA-256 (including iNES header): `7F9E40ADA806156D250803CEC9CC6F063E378028A561E0FDA018271A578FDD59`.
2. Select **one** IPS patch, and apply it to a **copy** of that original file with an IPS-compatible patcher.
3. Start the new game image in a compatible emulator or cartridge setup. Test the selection menu, both games, NPC interaction, and independent saving/reloading.
4. Preserve existing saves before switching editions.

Only **IPS delta files**, not game ROMs or prepatched images, belong in this directory. The earlier release pages remain available for historical provenance:

- [Demiforce Save and NPCFix](https://www.romhacking.net/translations/7555/)
- [USA Prototype Edition](https://www.romhacking.net/translations/7556/)
- [ChaosRush Edition](https://www.romhacking.net/translations/7557/)

## Future updates

**Keep the v1.0 patches unchanged.** If an edition needs changes, preserve its exact original IPS in Git history and publish a new patch file and documented version, including a new SHA-256 checksum and notes describing changes. Avoid replacing original bytes without a revision trail.
