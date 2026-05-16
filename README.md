# Integrasi TableMiner+ dan Self-Organizing Maps untuk Penemuan Data Semantik pada Medical Data Lake Menggunakan Dataset MIMIC

Repositori ini berisi kode sumber (*source code*) resmi dan arsitektur pipeline untuk melakukan pemetaan semantik otomatis (*Automated Semantic Data Discovery*) pada skema data lake kesehatan yang heterogen.

## Alur Sistem (Pipeline Architecture)
Sistem ini mengintegrasikan pendekatan heuristik berbasis aturan dan kecerdasan buatan (*Unsupervised Neural Network*) melalui 4 fase utama:

1. **Preprocessing (Data Discovery)**: Pemindaian direktori secara rekursif untuk mengumpulkan berkas relasional (`.csv`) dari klaster data klinis.
2. **Fase 1 (Initial Mapping)**: Ekstraksi skema *header* secara efisien (`nrows=0`) dan klasifikasi awal untuk memisahkan metadata berstatus *Generic* (bernama) dan *Unknown* (anonim).
3. **Fase 2 & 3 (TableMiner+ Heuristics)**: Proses kontekstualisasi, pemecahan ambiguitas (*disambiguation*), dan inferensi label semantik menggunakan basis pengetahuan (*Knowledge Base*).
4. **Fase 4 (SOM Clustering & Visualization)**: Pengelompokan fitur semantik hasil inferensi ke dalam grid 2D menggunakan *Self-Organizing Maps* (SOM) untuk menghasilkan representasi visual fitur (*Component Planes*).
5. **Fase 5 (Evaluation & Validation)**: Pengujian validitas dan akurasi hasil pemetaan semantik dengan membandingkan hasil inferensi terhadap berkas acuan `gold_standard.csv`.

## Struktur Repositori
* `main_experiment.ipynb` — Notebook utama eksekusi pipeline (Pre-processing dan Fase 1 - Fase 5).
* `sanity_check.ipynb` — Skrip pengujian validitas data dan modul.
* `medical_kb.json` — Basis pengetahuan lokal (*Knowledge Base*) untuk pemetaan semantik.
* `gold_standard.csv` — Data acuan validasi hasil inferensi.
* `output/` — Folder penyimpanan log statistik (`.json`/`.csv`) dan visualisasi peta (*heatmaps* gambar `.png`).
* `.gitignore` — Konfigurasi pembatasan pelacakan berkas besar dan lingkungan virtual.

## Dataset
Dataset klinis yang digunakan merupakan subset dari **MIMIC-III & MIMIC-IV** (100.000 data medis periode 2001-2019). 
* **Catatan**: Berkas data mentah tidak disertakan dalam repositori ini demi kepatuhan lisensi data medis dan batasan ukuran berkas. Datasets dapat diunduh secara mandiri melalui penyedia repositori publik (seperti Kaggle).


*Proyek ini dikembangkan menggunakan Python 3 dan pustaka visualisasi data/analisis matriks terkini.*