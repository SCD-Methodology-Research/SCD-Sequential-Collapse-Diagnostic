# Sequential Collapse Diagnostic (SCD) – Reproduction Package

This repository contains all data, code, and figures necessary to reproduce the
results presented in the paper:

> **"The Sequential Collapse Diagnostic (SCD): A Statistical Framework for
> Detecting Representation Collapse in High-Entropy Sequences"**
> Submitted for publication in an international peer-reviewed journal.

## Repository structure

```
.
├── data/
│   ├── Lotofacil.xlsx                # Lotofácil lottery draws (3,601 draws)
│   ├── ECG5000_TRAIN.ts              # ECG5000 training set
│   └── ECG5000_TEST.ts               # ECG5000 test set
├── notebooks/
│   ├── 01_transformer_causal.ipynb
│   ├── 02_phase_transition_plot.ipynb
│   ├── 03_R_ratio_comparison.ipynb
│   ├── 04_SCD_VQVAE_CPC.ipynb
│   ├── 05_rratio_null_histogram.ipynb
│   ├── 06_threshold_sensitivity.ipynb
│   ├── 07_scd_k_sensitivity.ipynb
│   ├── 08_scd_k_sensitivity_figure_table.ipynb
│   ├── 09_noise_robustness.ipynb
│   ├── 10_SCD_on_ECG5000_dataset.ipynb
│   ├── 11_lyapunov_vs_grt.ipynb
│   └── 12_SCD_ECG5000_multiseed_robustness.ipynb   # NEW (v4)
├── results/
│   ├── Figure_1_phase_transition_plot.tiff
│   ├── Figure_2_tsne_k4.tiff
│   ├── Figure_3_R_ratio_comparison_log.tiff
│   ├── Figure_4_GRT_vs_WW.tiff
│   ├── Figure_5_negative_control.tiff
│   ├── Figure_6_sp500.tiff
│   ├── Figure_7_ecg5000_sensitivity_Rratio.tiff
│   ├── Figure_8_lyapunov_vs_grt.tiff
│   ├── Figure_9_rratio_null_histogram.tiff
│   ├── Figure_10_left_noise_sensitivity_Rratio.tiff
│   ├── Figure_10_right_mixed_signal_Rratio.tiff
│   ├── Figure_11_scd_sensitivity_Rratio.tiff
│   ├── Figure_12_ecg5000_multiseed.pdf              # NEW (v4, vector)
│   ├── Figure_12_ecg5000_multiseed.png              # NEW (v4, raster 600 dpi)
│   ├── Figure_12_ecg5000_multiseed.tiff             # NEW (v4, raster 600 dpi)
│   ├── scd_sensitivity_table.csv
│   ├── ecg5000_multiseed_per_seed.csv               # NEW (v4)
│   ├── ecg5000_multiseed_aggregate.csv              # NEW (v4)
│   ├── ecg5000_multiseed_table.csv                  # NEW (v4, formatted)
│   ├── effect_vs_noise.json                         # NEW (v4)
│   └── table_multiseed.tex                          # NEW (v4)
├── requirements.txt
└── README.md
```

## Version 4 — Multi-seed robustness extension

Version 4 adds a 30-seed robustness study of the ECG5000 experiment (random
seeds 42–71), addressing the question of seed variability in the single-seed
ECG5000 results.

- **Notebook 12 (`12_SCD_ECG5000_multiseed_robustness.ipynb`)** repeats the
  ECG5000 autoencoder experiment across 30 seeds for each latent dimension
  (`d_model` ∈ {8, 16, 32}) and aggregates the SCD metrics. The notebook is
  self-contained: it parses the `.ts` files directly (no `sktime` dependency)
  and runs on CPU to preserve exact comparability with the published run.
- **Reproducibility check:** the seed-42 replicate reproduces the
  single-seed ECG5000 values reported in the paper exactly
  (`R_ratio` = 0.414 / 0.593 / 0.589). The measurement pipeline — autoencoder,
  per-series normalisation, K-means (`K=4`, `n_init=10`), and the SCD metric
  formulas — is unchanged from version 3.
- **Key finding:** the geometric metrics (effective rank, PC1 variance)
  separate `d_model = 8` from the higher dimensions robustly across seeds
  (PC1: 62.7 ± 4.6% vs 47.6 ± 4.4%), and the capacity-dependent increase in
  `R_ratio` is statistically reliable (Cohen's *d* = 0.95,
  Mann–Whitney *p* = 1.4 × 10⁻³). The binary NDC-6 verdict at `d_model = 8`
  is a boundary case (mean `R_ratio` = 0.508 ± 0.064; violated in 40% of seeds),
  consistent with NDC-6 being a conservative guideline rather than a sharp
  cut-off.
- **New artefacts:** `results/Figure_12_ecg5000_multiseed.{pdf,png,tiff}`,
  `results/ecg5000_multiseed_per_seed.csv`,
  `results/ecg5000_multiseed_aggregate.csv`, `results/ecg5000_multiseed_table.csv`,
  `results/effect_vs_noise.json`,
  and `results/table_multiseed.tex`.

This release **supplements and does not supersede** version 3; all previously
reported numbers remain valid as the seed-42 instance.

## Version 3 — Important corrections

Version 3 incorporates the following corrections identified during a
comprehensive audit of the manuscript and the codebase:

- **Notebook 04 (`04_SCD_VQVAE_CPC.ipynb`):** The `grt_pvalue` function has been
  rewritten to use the exact transition probability and variance formulas of
  Barton & David (1957) for sampling without replacement. The original
  implementation used an asymptotic approximation that assumed sampling with
  replacement. This correction does not affect any of the results reported in
  the paper: the normalised runs ratio (`R_ratio`), which is the basis of the
  NDC-6 criterion, was always computed correctly, and the corrected p-values
  remain at machine-precision zero for all collapsed models.
- **Figure 4 (`Figure_4_GRT_vs_WW.tiff`)** has been regenerated with the
  corrected implementation.
- **Notebook 11 (`11_lyapunov_vs_grt.ipynb`)** has been added to generate
  `Figure_8_lyapunov_vs_grt.tiff` using the corrected GRT.
- **Figure files use stable scientific names** (e.g.
  `Figure_8_lyapunov_vs_grt`), which are intentionally decoupled from the
  manuscript's appearance-order figure numbers. The full
  figure-number-to-filename correspondence is given in the
  "Figure mapping" section below and in the paper's Data Availability
  statement.

## Figure mapping (manuscript ↔ repository)

The manuscript numbers figures by order of appearance (Neurocomputing
`cas-dc` convention). This repository keeps stable, self-describing scientific
filenames so that the notebooks that *generate* each figure continue to write to
the same paths across versions 1–4. The two schemes correspond as follows.

| Manuscript figure | Repository file (scientific name)              | Generating notebook                         |
|-------------------|------------------------------------------------|---------------------------------------------|
| Fig. 1            | `Figure_1_phase_transition_plot.tiff`          | `02_phase_transition_plot.ipynb`            |
| Fig. 2            | `Figure_2_tsne_k4.tiff`                         | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 3            | `Figure_3_R_ratio_comparison_log.tiff`          | `03_R_ratio_comparison.ipynb`               |
| Fig. 4            | `Figure_4_GRT_vs_WW.tiff`                        | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 5            | `Figure_5_negative_control.tiff`                | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 6            | `Figure_8_lyapunov_vs_grt.tiff`                 | `11_lyapunov_vs_grt.ipynb`                   |
| Fig. 7 (a)        | `Figure_10_left_noise_sensitivity_Rratio.tiff`  | `09_noise_robustness.ipynb`                  |
| Fig. 7 (b)        | `Figure_10_right_mixed_signal_Rratio.tiff`      | `09_noise_robustness.ipynb`                  |
| Fig. 8            | `Figure_6_sp500.tiff`                           | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 9            | `Figure_7_ecg5000_sensitivity_Rratio.tiff`      | `10_SCD_on_ECG5000_dataset.ipynb`           |
| Fig. 10           | `Figure_12_ecg5000_multiseed.{pdf,png,tiff}`    | `12_SCD_ECG5000_multiseed_robustness.ipynb` |
| Fig. 11           | `Figure_9_rratio_null_histogram.tiff`           | `05_rratio_null_histogram.ipynb`            |
| Fig. A.1          | `Figure_11_scd_sensitivity_Rratio.tiff`         | `08_scd_k_sensitivity_figure_table.ipynb`   |

The journal-numbered figure files (`Figure_1.pdf` … `Figure_A1.pdf`) exist only
inside the Neurocomputing submission package and are **not** part of this
repository.

## Requirements

- Python 3.8 or higher
- Libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`,
  `torch`, `scipy`

Install dependencies with:

```bash
pip install -r requirements.txt
```

## Reproducing the results

1. **Clone this repository**

   ```bash
   git clone https://github.com/SCD-Methodology-Research/SCD-Sequential-Collapse-Diagnostic.git
   cd SCD-Sequential-Collapse-Diagnostic
   ```

2. **Run the notebooks** in `notebooks/`. For example, the single-seed ECG5000
   experiment:

   ```bash
   jupyter notebook notebooks/10_SCD_on_ECG5000_dataset.ipynb
   ```

   and the multi-seed robustness extension (version 4):

   ```bash
   jupyter notebook notebooks/12_SCD_ECG5000_multiseed_robustness.ipynb
   ```

## Data availability

This repository is permanently archived on Zenodo. Cite the **concept DOI**,
which always resolves to the latest version:

- **Zenodo (concept DOI):** [10.5281/zenodo.19931784](https://doi.org/10.5281/zenodo.19931784)
- Version 4 is published under its own version DOI, linked from the concept-DOI
  landing page. Version 4 **supplements and does not supersede** version 3; all
  previously archived versions remain citable.

Datasets used:

- **Lotofácil dataset** (`data/Lotofacil.xlsx`): 3,601 historical draws
  (15 numbers from 1 to 25 per draw). Publicly audited i.i.d. source.
- **ECG5000 dataset** (`data/ECG5000_TRAIN.ts`, `data/ECG5000_TEST.ts`):
  UCR Time Series Archive. 5,000 electrocardiogram time series of length 140,
  five heartbeat classes.

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE)
file for details.
