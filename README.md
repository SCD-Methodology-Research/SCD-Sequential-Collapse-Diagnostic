# Sequential Collapse Diagnostic (SCD) – Reproduction Package

This repository contains all data, code, and figures necessary to reproduce the results presented in the paper:

**"The Sequential Collapse Diagnostic (SCD): A Statistical Framework for Detecting Representation Collapse in High-Entropy Sequences"**  
*Submitted for publication in an international peer-reviewed journal.*

## Repository structure
```
.
├── data/
│ ├── Lotofacil.xlsx # Lotofácil lottery draws (3,601 draws, 15 numbers per draw)
│ ├── ECG5000_TRAIN.ts # ECG5000 training set (UCR Time Series Archive)
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
│ └── 10_SCD_on_ECG5000_dataset.ipynb # ECG5000 experiment
├── results/
│ ├── Figure_1_phase_transition_plot.png
│ ├── Figure_2_tsne_k4.png
│ ├── Figure_3_R_ratio_comparison_log.png
│ ├── Figure_4_GRT_vs_WW.png
│ ├── Figure_5_negative_control.png
│ ├── Figure_6_sp500.png
│ ├── Figure_7_lyapunov_vs_grt.png
│ ├── Figure_8_rratio_null_histogram.png
│ ├── Figure_9_left_noise_sensitivity_Rratio.png
│ ├── Figure_9_right_mixed_signal_Rratio.png
│ ├── Figure_10_scd_sensitivity_Rratio.png
│ ├── Figure_11_ecg5000_sensitivity_Rratio.png
│ └── scd_sensitivity_table.csv
├── requirements.txt
└── README.md```

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



