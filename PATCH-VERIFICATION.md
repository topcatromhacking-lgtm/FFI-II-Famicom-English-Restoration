# IPS patch verification

Verified on October 20, 2026 against the archive supplied by TopCat, `FF1&2 USA Prototype+ChaosRush+DemiforceFix.zip`. The original IPS bytes were not modified.

| Edition | Original filename | Size | SHA-256 |
| --- | --- | ---: | --- |
| Save and NPCFix | `Final Fantasy I & II (J) [T+Demiforce_v1.0]+SaveNPCFix-TopCat.ips` | 90,743 bytes | `bafa0d7ab67525d0b77469b3c1227566ab21ff676dc331203056a8f5c2fff102` |
| USA Prototype Edition | `Final Fantasy I & II USA Prototype Edition+Fix-TopCat.ips` | 127,123 bytes | `27b194b0cafcc7e3d9e46cff4bbabcffc825eaabf5aac73f3627b6ed1e93d44f` |
| ChaosRush Edition | `Final Fantasy I & II [ChaosRush1.3-2.2b+Menu-Grond+SaveNPCFix-TopCat.ips` | 69,701 bytes | `40961c1851926017279c8a8f94daa6c581e1576d69b50cada5318ce11fa01fbe` |

## Verification performed

The archive passed a ZIP CRC integrity check. All three IPS files contain the expected `PATCH` signature and `EOF` terminator, parse completely, have no unexpected trailing data, and have no overlapping records. All three contain the same NES 2.0 header modifications at offsets `0x06`–`0x0B`. The IPS files contain 480, 685, and 418 records, respectively.

These checks establish **file integrity and syntactic validity**, not gameplay correctness or independent authenticity against downloads from Romhacking.net. A full test requires patching a matching, legally obtained copy of the original Japanese compilation and running both games, including NPC dialogue and separate save/reload cycles.

**Repository status: published and verified.** All three original IPS files are now committed to [`patches/`](patches/) alongside [`SHA256SUMS.txt`](patches/SHA256SUMS.txt). On October 20, 2026, their GitHub Git blob SHA-1 identifiers were compared against Git blob identifiers independently computed from the **owner-supplied original IPS files**. All three match exactly, confirming byte-for-byte identity.

| Edition | Original file Git blob SHA-1 | GitHub file Git blob SHA-1 |
| --- | --- | --- |
| Save and NPCFix | `c01a8bc2a95050552df9f8562fffc9041d51af26` | **Match** |
| USA Prototype Edition | `c3016c1954619c81b998e0c3ac17a1c825cb134e` | **Match** |
| ChaosRush Edition | `e64005a3f2b40b187abb012817cf15658aa7902e` | **Match** |

Both checksums and patch bytes are preserved in Git version history. Neither ROMs nor prepatched ROM images belong in the repository. This verification is against the owner's archive, **not an independent re-download from Romhacking.net**.

## Selection screens

The original release notes state that **Save and NPCFix** and the **USA Prototype Edition** retain the vanilla selection menu without Grond's redesigned screen or dash feature. The **ChaosRush Edition** includes Grond's menu. This distinction should be preserved in the release documentation.
