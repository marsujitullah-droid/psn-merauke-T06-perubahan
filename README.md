# Label-Free Land-Clearing Detection in the Merauke PSN Area (T06)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24505783.svg)](https://doi.org/10.5281/zenodo.24505783)

Code, data and results for the study *"Detecting Land Clearing without Training Data in the Merauke National Strategic Project, Indonesia: Comparing Optical, Radar, Foundation-Model Embedding and Ensemble Methods"*.

> **Ringkasan (ID):** Repositori ini berisi notebook, sampel, dan tabel hasil untuk perbandingan tujuh metode deteksi pembukaan lahan tanpa data latih (CVA, dNDVI, PCA + k-means, Isolation Forest, log-ratio Sentinel-1, jarak embedding AlphaEarth, ensembel) di Blok E dan F kawasan PSN Merauke, 2023 vs 2025. Semua tabel dan gambar tersedia dalam versi Indonesia (_ID) dan Inggris (_EN).

## Study design

| Item | Value |
|---|---|
| Study area | Blocks E and F, 20 × 20 km each, Merauke Regency (next-ranked cells by 2024–2025 Hansen loss after Blocks A–D) |
| Periods | Dry season (Jun–Oct) 2023 vs 2025 |
| Methods | M1 CVA, M2 dNDVI, M3 PCA + k-means, M4 Isolation Forest (Sentinel-2); M5 log-ratio (Sentinel-1); M6 AlphaEarth cosine distance; M7 ensemble |
| Thresholds | Otsu, computed from 15,000 unlabelled pixels per block |
| Reference (evaluation only) | Consensus of Hansen GFC v1.13, RADD, JRC TMF (no field survey) |
| Evaluation | Precision, recall, F1, kappa, AUC, best-threshold F1, coverage, exact McNemar |

## Main results

Blocks E (139.097° E, 7.505° S; 935.6 ha Hansen loss 2024–2025) and F (140.729° E, 6.785° S; 721.4 ha). 1,500 change + 1,500 no-change reference points per block.

| Method | F1 E | F1 F | Mean F1 | Mean AUC | Coverage (%) |
|---|---|---|---|---|---|
| M1 CVA (S2) | 0.921 | 0.604 | 0.762 | 0.835 | 94.8 |
| M2 dNDVI (S2) | 0.919 | 0.677 | 0.798 | 0.821 | 94.8 |
| M3 PCA + k-means (S2) | 0.892 | 0.649 | 0.771 | 0.813 | 94.8 |
| M4 Isolation Forest (S2) | 0.919 | 0.587 | 0.753 | 0.855 | 94.8 |
| M5 S1 log-ratio | 0.480 | 0.537 | 0.509 | 0.718 | 100.0 |
| **M6 AlphaEarth embedding** | **0.951** | **0.892** | **0.922** | **0.977** | 100.0 |
| M7 Ensemble | 0.938 | 0.883 | 0.910 | 0.957 | 100.0 |

- M6 is significantly better than every other method in both blocks (exact McNemar, p < 0.001).
- Sentinel-2 methods drop sharply in Block F (AUC 0.67–0.75); 10.3% of Block F points have no cloud-free S2 data.
- Otsu thresholds lose up to 0.22 F1 versus the best threshold (S1 log-ratio, Block E).
- Detected change area in Block E (3,788–6,332 ha) is 4–7 × Hansen tree-cover loss (936 ha): label-free methods also capture non-forest clearing and other change.

## Repository structure

```
notebooks/T06_notebook.ipynb   full pipeline (Google Colab + Earth Engine + scikit-learn)
data/                          Block E/F boundaries, labelled and unlabelled samples, per-point scores
results/tables/                result tables and T06_hasil_ringkas.json
results/figures/               figures used in the manuscript
docs/diagrams/                 flowchart, context diagram, level-1 DFD (ID & EN)
```

## License

Code: MIT (`LICENSE`). Data, results and figures: CC BY 4.0.
