# Dataset T06 — Sampel Blok E dan F

Dihasilkan oleh notebook (`T06_hasil.zip` → `07_dataset/`).

| Berkas | Isi |
|---|---|
| `T06_sampel_berlabel.csv` | 1.500 titik/kelas/blok; `ref` (1 berubah, 0 tidak berubah), `blok`, `lon`, `lat`, selisih 6 band S2, NDVI, dB VV/VH, 64 embedding AlphaEarth 2023 dan 2025 |
| `T06_sampel_tanpa_label.csv` | 15.000 titik acak/blok tanpa label, dipakai untuk ambang Otsu, PCA, k-means, Isolation Forest, normalisasi ensembel |
| `T06_skor_dan_prediksi.csv` | Skor dan prediksi M1–M7 untuk setiap titik berlabel |
| `T06_blokE.geojson`, `T06_blokF.geojson` | Batas blok |

Nilai −9999 = tidak ada data (mis. tertutup awan). Lisensi CC BY 4.0.

**EN.** Labelled (1,500 per class per block) and unlabelled (15,000 per block) samples for Blocks E and F, per-point scores and predictions of methods M1–M7, and block boundaries. `ref`: 1 change, 0 no change; −9999 = no data. Licence CC BY 4.0.
