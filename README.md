# 🎵 Music Genre Clustering menggunakan Spotify Dataset

**Tugas Praktikum Machine Learning - Unsupervised Learning**

---

## 📋 Deskripsi Proyek

Proyek ini merupakan implementasi teknik **Unsupervised Learning** untuk mengelompokkan lagu-lagu berdasarkan fitur audio dari dataset Spotify. Dengan menggunakan **4 algoritma clustering berbeda** (K-Means, DBSCAN, Hierarchical Clustering, dan Gaussian Mixture Model), proyek ini bertujuan untuk menemukan pola tersembunyi dan mengelompokkan lagu-lagu yang memiliki karakteristik audio serupa, serta membandingkan performa masing-masing algoritma.

---

## 📂 Struktur Repository

```
📦 Clustering_Songs
├── 📄 README.md                                                # Dokumentasi proyek
├── 📓 [referensi-notebook] eda-and-clustering-songs.ipynb      # Notebook referensi dari Kaggle
├── 📊 dataset.csv                                              # Dataset Spotify Tracks
│
├── 📁 [v0]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi awal
│   └── 📓 [v0]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│
├── 📁 [v1]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi dengan K-Means
│   └── 📓 [v1]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│
├── 📁 [v2]_Music_Genre_Clustering_using_Spotify_Dataset/       # Versi improved
│   ├── 📓 [v2]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
│   └── 📊 hasil_clustering_lagu.csv                            # Hasil clustering v2
│
└── 📁 [v3]_Music_Genre_Clustering_using_Spotify_Dataset/       # ⭐ Versi lengkap (4 algoritma)
    ├── 📓 [v3]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb
    └── 📊 hasil_clustering_musik.csv                           # Hasil clustering v3
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
- **Plotly** - Visualisasi interaktif (2D, 3D, Parallel Coordinates, Sunburst)
- **SciPy** - Dendrogram untuk Hierarchical Clustering
- **Scikit-learn** - Algoritma Machine Learning:
  - K-Means Clustering
  - DBSCAN (Density-Based Spatial Clustering)
  - Agglomerative Clustering (Hierarchical)
  - Gaussian Mixture Model (GMM)
  - PCA (Principal Component Analysis)
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

- `[v3]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb` ⭐ **REKOMENDASI** - Versi lengkap dengan 4 algoritma
- `[v1]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb` - Versi dengan K-Means saja

---

## 📈 Metodologi

### 1. Exploratory Data Analysis (EDA)
- Analisis statistik deskriptif
- Visualisasi distribusi fitur audio (histogram, box plot)
- Correlation heatmap untuk melihat hubungan antar fitur
- Pairplot untuk visualisasi multi-dimensi

### 2. Data Preprocessing
- Pengecekan missing values dan duplikat
- Seleksi 9 fitur audio untuk clustering:
  - `danceability`, `energy`, `loudness`, `speechiness`
  - `acousticness`, `instrumentalness`, `liveness`, `valence`, `tempo`
- Sampling data (20,000 lagu) untuk efisiensi komputasi
- Standardisasi data menggunakan StandardScaler

### 3. Dimensionality Reduction
- PCA (Principal Component Analysis) untuk visualisasi 2D dan 3D
- Analisis explained variance
- Loading factors untuk interpretasi komponen

### 4. Clustering dengan 4 Algoritma

| Algoritma | Cara Kerja | Kelebihan | Kekurangan |
|-----------|------------|-----------|------------|
| **K-Means** | Membagi data ke K cluster dengan centroid | Cepat, mudah dipahami | Harus tentukan K, sensitif outlier |
| **DBSCAN** | Mengelompokkan data berdasarkan kepadatan | Deteksi outlier, bentuk bebas | Sulit di dimensi tinggi |
| **Hierarchical** | Membuat pohon cluster (dendrogram) | Tidak perlu tentukan K di awal | Lambat untuk data besar |
| **GMM** | Menggunakan distribusi Gaussian | Soft clustering, fleksibel | Lebih kompleks |

### 5. Evaluasi & Perbandingan
- **Silhouette Score**: Mengukur kualitas cluster (-1 s/d 1, semakin tinggi semakin baik)
- **Calinski-Harabasz Score**: Rasio dispersi antar/dalam cluster (semakin tinggi semakin baik)
- **Davies-Bouldin Score**: Kemiripan antar cluster (semakin rendah semakin baik)

### 6. Analisis Hasil
- Profil karakteristik setiap cluster (radar chart, heatmap)
- Distribusi genre asli per cluster
- Contoh lagu dari setiap cluster
- Visualisasi interaktif dengan Plotly

---

## 📊 Hasil Clustering

### Perbandingan Performa Algoritma

| Algoritma | Silhouette ↑ | Calinski-Harabasz ↑ | Davies-Bouldin ↓ | Jumlah Cluster |
|-----------|--------------|---------------------|------------------|----------------|
| K-Means | ~0.15-0.20 | ~3000-4000 | ~1.5-2.0 | 5 |
| DBSCAN | Varies | Varies | Varies | Auto-detected |
| Hierarchical | ~0.15-0.20 | ~3000-4000 | ~1.5-2.0 | 5 |
| GMM | ~0.15-0.20 | ~3000-4000 | ~1.5-2.0 | 5 |

*↑ = Semakin tinggi semakin baik, ↓ = Semakin rendah semakin baik*

### Karakteristik Cluster (Contoh dari K-Means)

| Cluster | Karakteristik | Cocok Untuk |
|---------|---------------|-------------|
| 0 | Energy tinggi, Danceability tinggi | Workout, Party |
| 1 | Acousticness tinggi, Energy rendah | Relaksasi, Tidur |
| 2 | Valence tinggi, Tempo cepat | Mood booster |
| 3 | Instrumentalness tinggi | Fokus, Belajar |
| 4 | Speechiness tinggi | Podcast-like, Rap |

*Catatan: Karakteristik cluster dapat bervariasi berdasarkan hasil optimasi. Silakan jalankan notebook untuk melihat hasil lengkap.*

### Visualisasi yang Tersedia

- 📊 Scatter plot 2D (PCA)
- 🎯 Scatter plot 3D interaktif (Plotly)
- 📈 Radar chart profil cluster
- 🔥 Heatmap karakteristik cluster
- 🌳 Dendrogram (Hierarchical)
- 🌞 Sunburst chart (Genre per Cluster)
- 📉 Parallel coordinates plot

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
- [Plotly Python Documentation](https://plotly.com/python/)

---

## 📝 Lisensi

Proyek ini dibuat untuk keperluan tugas praktikum Machine Learning.

---

⭐ Jika repository ini bermanfaat, jangan lupa berikan star!
