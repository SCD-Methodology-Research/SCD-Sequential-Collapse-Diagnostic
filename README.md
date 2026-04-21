# Sequential Collapse Diagnostic (SCD) – Reproduction Package

This repository contains all data, code, and figures necessary to reproduce the results presented in the paper:

**"The Sequential Collapse Diagnostic (SCD): A Statistical Framework for Detecting Representation Collapse in High-Entropy Sequences"**  
*Submitted to Chaos, Solitons & Fractals*

## Repository structure
```├── data/
│ └── Lotofacil.xlsx # Lotofácil lottery draws (3,601 draws, 15 numbers per draw)
├── notebooks/
│ ├── 01_transformer_causal.ipynb
│ ├── 02_phase_transition_plot.py
│ ├── 03_R_ratio_comparison.py
│ ├── 04_SCD_VQVAE_CPC.py
│ ├── 05_rratio_null_histogram.py
│ ├── 06_threshold_sensitivity.py
│ ├── 07_scd_k_sensitivity.py
│ ├── 08_scd_k_sensitivity_figure_table.py
│ └── 09_noise_robustness.py
├── results/
│ ├── phase_transition_plot.tiff
│ ├── tsne_k4.tiff
│ ├── R_ratio_comparison_log.tiff
│ ├── Figure_5_GRT_vs_WW.tiff
│ ├── Figure_6_negative_control.tiff
│ ├── Figure_7_sp500.tiff
│ ├── lyapunov_vs_grt.tiff
│ ├── rratio_null_histogram.tiff
│ ├── scd_sensitivity_Rratio.tiff
│ ├── noise_sensitivity_Rratio.tiff
│ ├── mixed_signal_Rratio.tiff
│ └── scd_sensitivity_table.csv
├── requirements.txt
└── README.md```

## Requirements

- Python 3.8 or higher
- Libraries: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `torch`, `scipy`

Install dependencies with:

```bash
pip install -r requirements.txt
