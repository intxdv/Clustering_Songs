# 🎵 Music Genre Clustering menggunakan Spotify Dataset

**Tugas Praktikum Machine Learning - Unsupervised Learning**

---

## 📋 Deskripsi Proyek

Proyek ini merupakan implementasi teknik **Unsupervised Learning** untuk mengelompokkan lagu-lagu berdasarkan fitur audio dari dataset Spotify. Proyek ini menggunakan pendekatan dengan fokus pada hasil yang **actionable** dan memiliki **nilai bisnis**, bukan hanya skor statistik tinggi.

### 🎯 Highlights Versi Terbaru (v4 - Advanced):
- **Stratified Sampling** untuk menjaga proporsi genre minoritas
- **Power Transform (Yeo-Johnson)** untuk mengatasi fitur skewed
- **Perbandingan Statistical vs Business Optimum** pada K-Means
- **PCA + DBSCAN** untuk mengatasi masalah "Giant Blob"
- **Radar Chart & Cluster Profiling** yang actionable untuk industri musik

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
├── 📓 [v4]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb  # ⭐ REKOMENDASI - Advanced Level
└── 📊 hasil_clustering_musik_v4.csv                            # Hasil clustering v4 (20,000 lagu)
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

- `[v4]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb` ⭐ **REKOMENDASI** - Versi Advanced 
- `[v3]_Music_Genre_Clustering_using_Spotify_Dataset/` - Versi dengan 4 algoritma clustering
- `[v1]_Music_Genre_Clustering_using_Spotify_Dataset/` - Versi basic dengan K-Means saja

---

## 📈 Metodologi (Versi 4 - Advanced)

### 1. Data Loading & Stratified Sampling
- Dataset: **114,000 lagu** dari **114 genre** berbeda
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
- **StandardScaler** setelah transformasi
- ⚠️ Mengapa penting? Algoritma berbasis jarak (K-Means) bekerja buruk pada data yang sangat miring

### 4. K-Means Clustering: Statistical vs Business Optimum

| Pendekatan | K | Silhouette Score | Insight |
|------------|---|------------------|---------|
| **Statistical** | 2 | 0.2015 (tertinggi) | Terlalu umum, tidak actionable |
| **Business** | 6 | 0.1593 | 6 micro-genres bermakna untuk industri |

**Key Insight**: Silhouette Score tinggi ≠ clustering yang baik untuk bisnis!

### 5. DBSCAN dengan PCA (Fixing the "Giant Blob")
- ❌ **Tanpa PCA**: 1 cluster raksasa (96.6% data) + noise
- ✅ **Dengan PCA 3D**: Mereduksi dimensi sebelum DBSCAN
- PCA menjelaskan **60.45%** varians dengan 3 komponen

### 6. Cluster Profiling & Labeling
- **Radar Chart** untuk visualisasi profil cluster
- **Automatic labeling** berdasarkan fitur dominan
- Analisis distribusi genre asli per cluster

---

## 📊 Hasil Clustering (Versi 4)

### 6 Cluster Labels (K-Means Business K=6)

| Cluster | Label | Top Genres | Karakteristik | Use Case |
|---------|-------|------------|---------------|----------|
| 0 | **High Energy / Instrumental** | Techno, Trance, Detroit Techno | Energy tinggi, Instrumentalness tinggi | Fokus, Workout elektronik |
| 1 | **High Energy / Fast Tempo** | Metalcore, Heavy Metal, Hardstyle | Energy sangat tinggi, Tempo cepat | Gym, Headbang |
| 2 | **High Energy Dance / Upbeat** | Comedy, Dancehall, J-Dance | Danceability tinggi, Speechiness tinggi | Party, Dance |
| 3 | **Acoustic** | Cantopop, Jazz, Mandopop | Acousticness tinggi, Energy rendah | Relaksasi, Kafe |
| 4 | **Low Energy / Acoustic / Instrumental** | New Age, Classical, Sleep, Ambient | Energy rendah, Acousticness & Instrumentalness tinggi | Tidur, Meditasi, Belajar |
| 5 | **High Energy Dance / Upbeat** | Salsa, Forró, Disco, House | Valence tinggi, Energy tinggi | Party, Mood booster |

### Distribusi Cluster

```
Cluster 0 (High Energy / Instrumental):     2,545 songs (12.7%)
Cluster 1 (High Energy / Fast Tempo):       3,818 songs (19.1%)
Cluster 2 (High Energy Dance / Upbeat):     2,882 songs (14.4%)
Cluster 3 (Acoustic):                       4,409 songs (22.0%)
Cluster 4 (Low Energy / Instrumental):      1,754 songs (8.8%)
Cluster 5 (High Energy Dance / Upbeat):     4,592 songs (23.0%)
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

| Aspek | Statistical Optimal (K=2) | Business Optimal (K=6) |
|-------|---------------------------|------------------------|
| Silhouette Score | 0.2015 (lebih tinggi) | 0.1593 |
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
