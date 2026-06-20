# Release Notes — v4

**Sequential Collapse Diagnostic (SCD) — Reproduction Package**
Repository: `SCD-Methodology-Research/SCD-Sequential-Collapse-Diagnostic`
Zenodo concept DOI: [10.5281/zenodo.19931784](https://doi.org/10.5281/zenodo.19931784)

---

## Summary

Version 4 adds a **30-seed robustness study** of the ECG5000 experiment and the
artefacts, figure, and table that support it in the manuscript. It also corrects
and clarifies repository documentation. **v4 supplements and does not supersede
v3**; all earlier versions remain citable under the concept DOI.

## What's new in v4

**Multi-seed robustness study (ECG5000, seeds 42–71)**
- `notebooks/12_SCD_ECG5000_multiseed_robustness.ipynb` — self-contained,
  CPU-only, parses `.ts` files directly (no `sktime` dependency).
- `results/ecg5000_multiseed_per_seed.csv` — per-seed metrics (30 seeds).
- `results/ecg5000_multiseed_aggregate.csv` — mean ± SD, [min, max], CV,
  effective rank, PC1 variance, and NDC-6 violation rate per latent dimension.
- `results/ecg5000_multiseed_table.csv` — the same aggregate values in
  publication-formatted strings (e.g. `0.508 +/- 0.064`, `40%`).
- `results/effect_vs_noise.json` — effect-size summary (Cohen's d = 0.95,
  Mann–Whitney p = 1.4 × 10⁻³ for d_model = 8 vs 16).
- `results/Figure_12_ecg5000_multiseed.{pdf,png,tiff}` — three-panel multi-seed
  figure (corresponds to **Figure 10** in the manuscript).
- `results/table_multiseed.tex` — multi-seed summary table, aligned to the final
  manuscript table.

## Documentation corrections

- `README.md` — clarified that repository figure files keep **stable scientific
  filenames**, intentionally decoupled from the manuscript's appearance-order
  figure numbers; added a **Figure mapping** section; Data availability now
  cites the Zenodo **concept DOI**.
- `FIGURE_MAPPING.md` — new file: manuscript-figure-number ↔ repository-filename
  ↔ generating-notebook table.
- `MANIFEST_v4.sha256` — SHA-256 checksums for integrity verification.

## Key result (reported in the manuscript)

The geometric metrics separate `d_model = 8` from higher dimensions robustly
across seeds (PC1 variance 62.7 ± 4.6 % vs 47.6 ± 4.4 %; effective rank
8.0 → 15.8 → 19.9). The capacity-dependent trend in R_ratio is statistically
significant (Cohen's d = 0.95; Mann–Whitney p = 1.4 × 10⁻³). The binary NDC-6
verdict at `d_model = 8` is a **boundary case** (mean R_ratio = 0.508 ± 0.064;
violated in 40 % of seeds), reframed as capacity-critical — consistent with the
composite-diagnostic thesis. Seed 42 reproduces the originally published
single-seed values exactly (0.414 / 0.593 / 0.589).

## Reproducibility

```bash
pip install -r requirements.txt          # from the v3 base repository
jupyter notebook notebooks/12_SCD_ECG5000_multiseed_robustness.ipynb
```

Running notebook 12 regenerates the CSVs, the JSON, and
`Figure_12_ecg5000_multiseed.{pdf,png,tiff}` to the paths above (the notebook's
`savefig` targets these scientific filenames).

## Integrity

```bash
sha256sum -c MANIFEST_v4.sha256
```

## Compatibility

- Additive over v3; no v1–v3 file is renamed, moved, or removed.
- Figure filenames unchanged from earlier versions, preserving any external
  references that pin a v1–v3 filename.

## Not included / unchanged from v3

Datasets (`data/`), notebooks 01–11, `requirements.txt`, `LICENSE`, and results
figures 1–11 are unchanged and remain in the base repository.
