# 🎵 Music Genre Clustering menggunakan Spotify Dataset

**Tugas Praktikum Machine Learning - Unsupervised Learning**

---

## 📋 Deskripsi Proyek

Proyek ini merupakan implementasi teknik **Unsupervised Learning** untuk mengelompokkan lagu-lagu berdasarkan fitur audio dari dataset Spotify. Proyek ini menggunakan pendekatan dengan fokus pada hasil yang **actionable** dan memiliki **nilai bisnis**, bukan hanya skor statistik tinggi.

### 🎯 Highlights Versi Terbaru (v5 - Senior DS Level):
- **Stratified Sampling** untuk menjaga proporsi genre minoritas
- **Power Transform (Yeo-Johnson)** dengan analisis skewness (1.40 → 0.32)
- **Data-Driven K Selection** menggunakan 3 metrik: Silhouette, Calinski-Harabasz, Davies-Bouldin
- **Perbandingan Head-to-Head** K=2 (Statistical) vs K=5 (Business Optimal)
- **PCA + DBSCAN** untuk mengatasi masalah "Giant Blob"
- **Radar Chart Interaktif (Plotly)** & Cluster Profiling
- **Critical Analysis** - evaluasi jujur kelebihan dan keterbatasan setiap model

---

## 📂 Struktur Repository

```
📦 Clustering_Songs
├── 📄 README.md                                                # Dokumentasi proyek
├── 📓 [referensi-notebook] eda-and-clustering-songs.ipynb      # Notebook referensi dari Kaggle
├── 📊 dataset.csv                                              # Dataset Spotify Tracks (114,000 lagu)
│
├── 📁 [v0]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi awal (eksplorasi)
│   └── 📓 [v0]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│
├── 📁 [v1]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi dengan K-Means dasar
│   └── 📓 [v1]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│
├── 📁 [v2]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi improved
│   ├── 📓 [v2]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│   └── 📊 hasil_clustering_lagu.csv                            # Hasil clustering v2
│
├── 📁 [v3]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi 4 algoritma
│   ├── 📓 [v3]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│   └── 📊 hasil_clustering_musik.csv                           # Hasil clustering v3
│
├── 📁 [v4]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi Advanced
│   ├── 📓 [v4]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│   └── 📊 hasil_clustering_musik_v4.csv                        # Hasil clustering v4
│
├── 📓 [v5]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb  # ⭐ REKOMENDASI - Senior DS Level
└── 📊 hasil_clustering_musik_v5.csv                            # Hasil clustering v5 (20,000 lagu)
```

---

## 📊 Dataset

Dataset yang digunakan adalah **Spotify Tracks Dataset** yang berisi fitur audio dari ribuan lagu yang diambil menggunakan Spotify Web API.

### Fitur Dataset

| Fitur | Deskripsi |
|-------|-----------|
| `track_id` | ID unik lagu di Spotify |
| `artists` | Nama artis |
| `album_name` | Nama album |
| `track_name` | Nama lagu |
| `popularity` | Popularitas lagu (0-100) |
| `duration_ms` | Durasi lagu dalam milidetik |
| `explicit` | Konten eksplisit (True/False) |
| `danceability` | Seberapa cocok lagu untuk menari (0.0-1.0) |
| `energy` | Intensitas dan aktivitas lagu (0.0-1.0) |
| `key` | Kunci nada lagu |
| `loudness` | Kekerasan rata-rata dalam dB |
| `mode` | Modalitas lagu (mayor=1, minor=0) |
| `speechiness` | Keberadaan kata-kata yang diucapkan (0.0-1.0) |
| `acousticness` | Tingkat akustik lagu (0.0-1.0) |
| `instrumentalness` | Tingkat instrumental (0.0-1.0) |
| `liveness` | Keberadaan penonton dalam rekaman (0.0-1.0) |
| `valence` | Positifitas musik (0.0-1.0) |
| `tempo` | Tempo lagu dalam BPM |
| `time_signature` | Tanda birama |
| `track_genre` | Genre lagu |

---

## 🔧 Teknologi & Library

- **Python 3.x**
- **Pandas** - Manipulasi dan analisis data
- **NumPy** - Operasi numerik
- **Matplotlib & Seaborn** - Visualisasi data statis
- **Plotly** - Visualisasi interaktif (2D, 3D, Parallel Coordinates, Sunburst, Radar Chart)
- **SciPy** - Dendrogram untuk Hierarchical Clustering, Statistik dan analisis skewness
- **Scikit-learn** - Algoritma Machine Learning:
  - K-Means Clustering
  - DBSCAN (Density-Based Spatial Clustering)
  - Agglomerative Clustering (Hierarchical)
  - Gaussian Mixture Model (GMM)
  - PCA (Principal Component Analysis)
  - PowerTransformer (Yeo-Johnson)
  - StandardScaler
  - Metrik Evaluasi (Silhouette, Calinski-Harabasz, Davies-Bouldin)

---

## 🚀 Cara Menjalankan

### 1. Clone Repository

```bash
git clone https://github.com/intxdv/Clustering_Songs.git
cd Clustering_Songs
```

### 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn scipy
```

### 3. Jalankan Notebook

Buka notebook menggunakan Jupyter Notebook, JupyterLab, atau VS Code:

- `[v5]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb` ⭐ **REKOMENDASI** - Senior DS Level
- `[v4]_Music_Genre_Clustering_using_Spotify_Dataset/` - Versi Advanced
- `[v3]_Music_Genre_Clustering_using_Spotify_Dataset/` - Versi dengan 4 algoritma clustering
- `[v2]_Music_Genre_Clustering_using_Spotify_Dataset/` - Versi improved dengan export CSV
- `[v1]_Music_Genre_Clustering_using_Spotify_Dataset/` - Versi basic dengan K-Means saja

---

## 📈 Metodologi (Versi 5 - Senior DS Level)

### 1. Data Loading & Stratified Sampling
- Dataset: **114,000 lagu** dari **114 genre** berbeda (perfectly balanced: 1,000 lagu/genre)
- **Stratified Sampling** 20,000 lagu untuk menjaga proporsi genre minoritas
- Tidak menggunakan random sampling biasa agar genre langka tidak hilang

### 2. Exploratory Data Analysis (EDA)
- Analisis distribusi fitur audio dengan **skewness analysis**
- Correlation heatmap untuk melihat hubungan antar fitur
- Identifikasi **4 fitur highly skewed**: `loudness`, `speechiness`, `instrumentalness`, `liveness`

### 3. Advanced Preprocessing (Crucial Step)
- **Power Transform (Yeo-Johnson)** untuk fitur skewed
  - Yeo-Johnson dapat menangani nilai negatif (seperti loudness)
  - Mendekatkan distribusi ke Gaussian (normal)
  - **Rata-rata skewness: 1.40 → 0.32** (pengurangan 77%)
- **StandardScaler** setelah transformasi
- ⚠️ Mengapa penting? Algoritma berbasis jarak (K-Means) bekerja buruk pada data yang sangat miring

### 4. K-Means Clustering: Data-Driven K Selection

**Evaluasi K=2 hingga K=15** menggunakan 3 metrik:
- **Silhouette Score** - Mengukur kohesi dan separasi cluster
- **Calinski-Harabasz Index** - Rasio dispersi antar dan dalam cluster
- **Davies-Bouldin Index** - Mengukur kemiripan antar cluster (lebih rendah = lebih baik)

| Pendekatan | K | Silhouette Score | Penurunan dari K=2 | Insight |
|------------|---|------------------|--------------------|---------|
| **Statistical** | 2 | 0.2015 (tertinggi) | - | Terlalu umum, tidak actionable |
| **Business** | 5 | 0.1625 | -3.9% | 5 micro-genres bermakna untuk industri |

**Key Insight**: K=5 dipilih karena penurunan Silhouette hanya 3.9% dari K=2, namun memberikan 5 cluster yang actionable!

### 5. DBSCAN dengan PCA (Fixing the "Giant Blob")
- ❌ **Tanpa PCA**: 1 cluster raksasa (98%+ data) sebagai noise
- ✅ **Dengan PCA 3D**: Mereduksi dimensi sebelum DBSCAN
- PCA menjelaskan **60.5%** varians dengan 3 komponen
- Parameter tuning: eps=0.35, min_samples=30 → 6 clusters, 20.4% noise

### 6. Cluster Profiling & Labeling
- **Radar Chart** untuk visualisasi profil cluster
- **Automatic labeling** berdasarkan fitur dominan
- Analisis distribusi genre asli per cluster

---

## 📊 Hasil Clustering (Versi 5)

### 5 Cluster Labels (K-Means Business K=5)

| Cluster | Label | Karakteristik | Use Case |
|---------|-------|---------------|----------|
| 0 | **High-Energy / Fast / Live** | Energy tinggi, Tempo cepat, Liveness tinggi | Gym, Concert vibes |
| 1 | **Acoustic / Slow** | Acousticness tinggi, Tempo lambat | Relaksasi, Kafe, Belajar |
| 2 | **High-Energy / Instrumental / Melancholic** | Energy tinggi, Instrumentalness tinggi, Valence rendah | Fokus, Workout elektronik |
| 3 | **Calm / Acoustic / Instrumental** | Energy rendah, Acousticness & Instrumentalness tinggi | Tidur, Meditasi, Ambient |
| 4 | **Dance-Party / Vocal-Heavy** | Danceability tinggi, Valence tinggi, Speechiness tinggi | Party, Mood booster |

### Distribusi Cluster

```
Cluster 0 (High-Energy / Fast / Live):              5,094 songs (25.5%)
Cluster 1 (Acoustic / Slow):                        5,068 songs (25.3%)
Cluster 2 (High-Energy / Instrumental / Melancholic): 2,604 songs (13.0%)
Cluster 3 (Calm / Acoustic / Instrumental):         1,796 songs (9.0%)
Cluster 4 (Dance-Party / Vocal-Heavy):              5,438 songs (27.2%)
```

### Visualisasi yang Tersedia

- 📊 Histogram distribusi fitur (Before & After Transform)
- 🔗 Correlation Heatmap
- 📈 Elbow Method & Silhouette Score Plot
- 🎯 Scatter plot 2D (PCA) - Statistical vs Business K
- 📡 3D Interactive Plot (DBSCAN results)
- 🎭 Radar Chart profil cluster
- 🔥 Heatmap karakteristik cluster
- 📊 Silhouette Analysis per cluster

---

## 💡 Key Insights & Lessons Learned

### Mengapa Silhouette Score Bisa Menipu?

1. **DBSCAN Silhouette Inflation**: Noise points dikeluarkan dari perhitungan, sehingga cluster yang tersisa terlihat "perfect"
2. **K-Means dengan K kecil**: K=2 sering menghasilkan skor tertinggi, tapi pemisahan terlalu umum (misal: "musik cepat" vs "musik lambat")
3. **Trade-off**: Separasi matematis tinggi ≠ Segmentasi yang berguna untuk bisnis

### Business vs Statistical Trade-off

| Aspek | Statistical Optimal (K=2) | Business Optimal (K=5) |
|-------|---------------------------|------------------------|
| Silhouette Score | 0.2015 (lebih tinggi) | 0.1625 (-3.9%) |
| Interpretabilitas | Rendah | **Tinggi** |
| Actionability | Rendah | **Tinggi** |
| Nilai Bisnis | Rendah | **Tinggi** |

### Aplikasi Praktis untuk Spotify/Music Platform

- 🎧 **Playlist Generation** - Otomatis membuat playlist berdasarkan cluster
- 🔍 **Music Discovery** - Rekomendasi lagu dari cluster yang sama
- 📈 **User Segmentation** - Memahami preferensi pengguna berdasarkan cluster favorit
- 🎯 **Targeted Marketing** - Kampanye iklan berdasarkan micro-genre preference

---

## 👥 Identitas Kelompok

- **Lab:** Pembelajaran Mesin E2
- **Anggota 1:**
  - Nama: Sulhan Fuadi
  - NIM: 24060123130115
- **Anggota 2:**
  - Nama: Syafiq Abiyyu Taqi
  - NIM: 24060123120012

---

## 📚 Referensi

- [Spotify Tracks Dataset - Kaggle](https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset)
- [Scikit-learn Documentation](https://scikit-learn.org/)
- [K-Means Clustering](https://scikit-learn.org/stable/modules/clustering.html#k-means)
- [DBSCAN Clustering](https://scikit-learn.org/stable/modules/clustering.html#dbscan)
- [Hierarchical Clustering](https://scikit-learn.org/stable/modules/clustering.html#hierarchical-clustering)
- [Gaussian Mixture Models](https://scikit-learn.org/stable/modules/mixture.html)
- [Power Transformer (Yeo-Johnson)](https://scikit-learn.org/stable/modules/preprocessing.html#mapping-to-a-gaussian-distribution)
- [PCA - Principal Component Analysis](https://scikit-learn.org/stable/modules/decomposition.html#pca)
- [Plotly Python Documentation](https://plotly.com/python/)
- [Silhouette Score Interpretation](https://scikit-learn.org/stable/modules/clustering.html#silhouette-coefficient)

---

## 📝 Lisensi

Proyek ini dibuat untuk keperluan tugas praktikum Machine Learning.

---

⭐ Jika repository ini bermanfaat, jangan lupa berikan star!
