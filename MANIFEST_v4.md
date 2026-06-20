# MANIFEST — SCD Reproduction Package, GitHub/Zenodo v4

Generated: 2026-06-20
Package: `v4_github_upload.zip` (delta over v3 base repository)
Total files: 12 · Total size: 2,790,063 bytes

This package is **additive**: it layers on the existing v3 repository. Files not listed here (datasets, notebooks 01–11, requirements.txt, LICENSE, results figures 1–11) are unchanged from v3 and remain in the base repository.

All `Figure_12_ecg5000_multiseed.{pdf,png,tiff}` figures, the multi-seed CSVs (`per_seed`, `aggregate`, `table`), `effect_vs_noise.json`, and `table_multiseed.tex` are produced directly by `notebooks/12_SCD_ECG5000_multiseed_robustness.ipynb`.

## File inventory (SHA-256)

| File | Size (bytes) | Role | SHA-256 |
|---|---:|---|---|
| `FIGURE_MAPPING.md` | 2,728 | NEW (v4 doc) | `25801a6e83eb124d6ca53c3bff1d09825dd138f5e161d88c5b3a2def2c9c2843` |
| `MANIFEST_v4.sha256` | 1,099 | NEW (v4 checksums) | `55e4c00c3b20c413bafa35a5ad37822ad5370ccd52ea01fd60aa6bb3b5e7de17` |
| `README.md` | 9,718 | UPDATED (v4) | `49411ebecc4936cbd1a92ed91dc9c40223a172e560ad9979cd20eaf4fc820e08` |
| `notebooks/12_SCD_ECG5000_multiseed_robustness.ipynb` | 14,365 | NEW (v4 data/code) | `1fa71402988d62f41c48e828c759d389417e82150356709381c687653cf542ed` |
| `results/Figure_12_ecg5000_multiseed.pdf` | 20,732 | NEW (v4 data/code) | `9ce308bec7b1e5aafc774e0e88dd9144619459ee36564a451385163d8386913c` |
| `results/Figure_12_ecg5000_multiseed.png` | 218,999 | NEW (v4 data/code) | `a807740b89ca8b1a6f5692cfd2370f4f292c63a320b7ce8745dab1f3cd35143f` |
| `results/Figure_12_ecg5000_multiseed.tiff` | 2,513,042 | NEW (v4 data/code) | `0962f8cd9ccd6fd5fd11ce4c3a8a72f301b17ac5bc8695d67ea6367a6652faf1` |
| `results/ecg5000_multiseed_aggregate.csv` | 980 | NEW (v4 data/code) | `f0f1d7b299bc460740824bc9c89c989d162e7a6df544f55e11d3baabefe244af` |
| `results/ecg5000_multiseed_per_seed.csv` | 4,671 | NEW (v4 data/code) | `02fe28e1cb5287e7990af12ab7231829e908cb6b73e241eccfccf6a1bd468af8` |
| `results/ecg5000_multiseed_table.csv` | 314 | NEW (v4 data/code) | `e161aa84a44429f110679dcf82d3198382fd1b23f260e6fcca08f42634e18a14` |
| `results/effect_vs_noise.json` | 105 | NEW (v4 data/code) | `9a2b8ef2145964d659c92e61f5a322bb231806fe04674dfba69633bf6675001d` |
| `results/table_multiseed.tex` | 3,310 | NEW (v4 data/code) | `b4237c21b143570a65a74157b0124ba8eeda78797bdbf80f62f2f65d438d536c` |

## Verification

From the package root:

```bash
sha256sum -c MANIFEST_v4.sha256
```

## Provenance notes

- `README.md` — corrected v4 (figure-naming policy clarified, Figure-mapping section added, Data availability cites the Zenodo **concept DOI**).
- `results/Figure_12_ecg5000_multiseed.{pdf,png,tiff}` — three formats, all written by notebook 12 (`pdf` vector; `png`/`tiff` raster at 600 dpi).
- `results/ecg5000_multiseed_table.csv` — publication-formatted aggregate; archival artefact produced by notebook 12; values identical to `ecg5000_multiseed_aggregate.csv`.
- `results/table_multiseed.tex` — LaTeX version of the same table; matches the final manuscript.
- `FIGURE_MAPPING.md` — manuscript-figure-number ↔ repository-filename table.
