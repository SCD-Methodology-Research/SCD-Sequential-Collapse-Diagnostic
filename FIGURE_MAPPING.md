# Figure mapping — manuscript number ↔ repository filename

The manuscript numbers figures by order of appearance (Neurocomputing
`cas-dc` convention). The repository keeps stable, self-describing scientific
filenames so that the notebooks that *generate* each figure continue to write
to the same paths across versions 1–4. The two schemes correspond as follows.

| Manuscript figure | Repository file (scientific name)            | Generating notebook                         |
|-------------------|-----------------------------------------------|---------------------------------------------|
| Fig. 1            | `Figure_1_phase_transition_plot.tiff`         | `02_phase_transition_plot.ipynb`            |
| Fig. 2            | `Figure_2_tsne_k4.tiff`                        | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 3            | `Figure_3_R_ratio_comparison_log.tiff`         | `03_R_ratio_comparison.ipynb`               |
| Fig. 4            | `Figure_4_GRT_vs_WW.tiff`                       | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 5            | `Figure_5_negative_control.tiff`               | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 6            | `Figure_8_lyapunov_vs_grt.tiff`                | `11_lyapunov_vs_grt.ipynb`                   |
| Fig. 7 (panel a)  | `Figure_10_left_noise_sensitivity_Rratio.tiff` | `09_noise_robustness.ipynb`                  |
| Fig. 7 (panel b)  | `Figure_10_right_mixed_signal_Rratio.tiff`     | `09_noise_robustness.ipynb`                  |
| Fig. 8            | `Figure_6_sp500.tiff`                          | `04_SCD_VQVAE_CPC.ipynb`                     |
| Fig. 9            | `Figure_7_ecg5000_sensitivity_Rratio.tiff`     | `10_SCD_on_ECG5000_dataset.ipynb`           |
| Fig. 10           | `Figure_12_ecg5000_multiseed.{pdf,png,tiff}`       | `12_SCD_ECG5000_multiseed_robustness.ipynb` |
| Fig. 11           | `Figure_9_rratio_null_histogram.tiff`          | `05_rratio_null_histogram.ipynb`            |
| Fig. A.1          | `Figure_11_scd_sensitivity_Rratio.tiff`        | `08_scd_k_sensitivity_figure_table.ipynb`   |

**Why the numbers differ from the filenames.** Manuscript figure numbers are a
property of one paper layout (they shift if sections are reordered), whereas the
repository filenames are tied to the experiments and to the `savefig(...)` calls
inside the notebooks. Decoupling the two keeps the reproduction pipeline stable
and preserves compatibility with versions 1–3 (and with any external work that
cites a v1–v3 filename). The journal-numbered figure files
(`Figure_1.pdf` … `Figure_A1.pdf`) exist only inside the Neurocomputing
submission package and are not part of this repository.
