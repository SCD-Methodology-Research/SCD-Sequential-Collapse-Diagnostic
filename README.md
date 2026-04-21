# Sequential Collapse Diagnostic (SCD) – Reproduction Package

This repository contains all data, code, and figures necessary to reproduce the results presented in the paper:

**"The Sequential Collapse Diagnostic (SCD): A Statistical Framework for Detecting Representation Collapse in High-Entropy Sequences"**  
*Submitted to Chaos, Solitons & Fractals*

## Repository structure
```
├── data/
│ └── Lotofacil.xlsx # Lotofácil lottery draws (3,601 draws, 15 numbers per draw)
├── notebooks/
│ ├── 01_transformer_causal.ipynb
│ ├── 02_phase_transition_plot.ipynb
│ ├── 03_R_ratio_comparison.ipynb
│ ├── 04_SCD_VQVAE_CPC.ipynb
│ ├── 05_rratio_null_histogram.ipynb
│ ├── 06_threshold_sensitivity.ipynb
│ ├── 07_scd_k_sensitivity.ipynb
│ ├── 08_scd_k_sensitivity_figure_table.ipynb
│ └── 09_noise_robustness.ipynb
├── results/
│ ├── Figure_1_phase_transition_plot.tiff
│ ├── Figure_2_tsne_k4.tiff
│ ├── Figure_3_R_ratio_comparison_log.tiff
│ ├── Figure_4_GRT_vs_WW.tiff
│ ├── Figure_5_negative_control.tiff
│ ├── Figure_6_sp500.tiff
│ ├── Figure_7_lyapunov_vs_grt.tiff
│ ├── Figure_8_rratio_null_histogram.tiff
│ ├── Figure_9_left_noise_sensitivity_Rratio.tiff
│ ├── Figure_9_right_mixed_signal_Rratio.tiff
│ ├── Figure_10_scd_sensitivity_Rratio.tiff
│ └── scd_sensitivity_table.csv
├── requirements.txt
└── README.md```

## Requirements

- Python 3.8 or higher
- Libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `torch`, `scipy`

Install dependencies with:

```bash
pip install -r requirements.txt
