# Sequential Collapse Diagnostic (SCD) – Reproduction Package

This repository contains all data, code, and figures necessary to reproduce the results presented in the paper:

**"The Sequential Collapse Diagnostic (SCD): A Statistical Framework for Detecting Representation Collapse in High-Entropy Sequences"**  
*Submitted for publication in an international peer-reviewed journal.*

## Repository structure
```
.
├── data/
│ ├── Lotofacil.xlsx # Lotofácil lottery draws (3,601 draws)
│ ├── ECG5000_TRAIN.ts # ECG5000 training set
│ └── ECG5000_TEST.ts # ECG5000 test set
├── notebooks/
│ ├── 01_transformer_causal.ipynb
│ ├── 02_phase_transition_plot.ipynb
│ ├── 03_R_ratio_comparison.ipynb
│ ├── 04_SCD_VQVAE_CPC.ipynb
│ ├── 05_rratio_null_histogram.ipynb
│ ├── 06_threshold_sensitivity.ipynb
│ ├── 07_scd_k_sensitivity.ipynb
│ ├── 08_scd_k_sensitivity_figure_table.ipynb
│ ├── 09_noise_robustness.ipynb
│ ├── 10_SCD_on_ECG5000_dataset.ipynb
│ └── 11_lyapunov_vs_grt.ipynb
├── results/
│ ├── Figure_1_phase_transition_plot.tiff
│ ├── Figure_2_tsne_k4.tiff
│ ├── Figure_3_R_ratio_comparison_log.tiff
│ ├── Figure_4_GRT_vs_WW.tiff
│ ├── Figure_5_negative_control.tiff
│ ├── Figure_6_sp500.tiff
│ ├── Figure_7_ecg5000_sensitivity_Rratio.tiff
│ ├── Figure_8_lyapunov_vs_grt.tiff
│ ├── Figure_9_rratio_null_histogram.tiff
│ ├── Figure_10_left_noise_sensitivity_Rratio.tiff
│ ├── Figure_10_right_mixed_signal_Rratio.tiff
│ ├── Figure_11_scd_sensitivity_Rratio.tiff
│ └── scd_sensitivity_table.csv
├── requirements.txt
└── README.md```

## Version 3 — Important corrections

Version 3 incorporates the following corrections identified during a
comprehensive audit of the manuscript and the codebase:

- **Notebook 04 (`04_SCD_VQVAE_CPC.ipynb`):** The `grt_pvalue` function
  has been rewritten to use the exact transition probability and variance
  formulas of Barton & David (1957) for sampling without replacement.
  The original implementation used an asymptotic approximation that
  assumed sampling with replacement. This correction does not affect any
  of the results reported in the paper: the normalised runs ratio
  (`R_ratio`), which is the basis of the NDC‑6 criterion, was always
  computed correctly, and the corrected p‑values remain at
  machine‑precision zero for all collapsed models.

- **Figure 4 (`Figure_4_GRT_vs_WW.tiff`)** has been regenerated with the
  corrected implementation.

- **Notebook 11 (`11_lyapunov_vs_grt.ipynb`)** has been added to
  generate `Figure_8_lyapunov_vs_grt.tiff` using the corrected GRT.

- **Figure numbering** has been updated to match the final manuscript.

## Requirements

- Python 3.8 or higher
- Libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `torch`, `scipy`

Install dependencies with:

```bash
pip install -r requirements.txt

## Reproducing the results

1. **Clone this repository**  
   ```bash
   git clone https://github.com/SCD-Methodology-Research/SCD-Sequential-Collapse-Diagnostic.git
   cd SCD-Sequential-Collapse-Diagnostic

jupyter notebook notebooks/10_SCD_on_ECG5000_dataset.ipynb

## Data availability

- **Lotofácil dataset** (`data/Lotofacil.xlsx`): 3,601 historical draws (15 numbers from 1 to 25 per draw). Publicly audited i.i.d. source.  
- **ECG5000 dataset** (`data/ECG5000_TRAIN.ts`, `data/ECG5000_TEST.ts`): UCR Time Series Archive. 5,000 electrocardiogram time series of length 140, five heartbeat classes.

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.



