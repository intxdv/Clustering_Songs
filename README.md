# 🎵 Music Genre Clustering menggunakan Spotify Dataset

**Tugas Praktikum Machine Learning - Unsupervised Learning**

---

## 📋 Deskripsi Proyek

Proyek ini merupakan implementasi teknik **Unsupervised Learning** untuk mengelompokkan lagu-lagu berdasarkan fitur audio dari dataset Spotify. Dengan menggunakan algoritma **K-Means Clustering**, proyek ini bertujuan untuk menemukan pola tersembunyi dan mengelompokkan lagu-lagu yang memiliki karakteristik audio serupa.

---

## 📂 Struktur Repository

```
📦 Clustering_Songs
├── 📄 README.md                                            # Dokumentasi proyek
├── 📓 [referensi-notebook] eda-and-clustering-songs.ipynb  # Notebook referensi dari Kaggle
├── 📓 [v0]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb  # Versi awal notebook
├── 📓 [v1]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb  # Versi final notebook
└── 📊 dataset.csv                                          # Dataset Spotify Tracks
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
- **Matplotlib & Seaborn** - Visualisasi data
- **Plotly** - Visualisasi interaktif
- **Scikit-learn** - Algoritma Machine Learning
  - K-Means Clustering
  - PCA (Principal Component Analysis)
  - StandardScaler
  - Silhouette Score

---

## 🚀 Cara Menjalankan

### 1. Clone Repository

```bash
git clone https://github.com/intxdv/Clustering_Songs.git
cd Clustering_Songs
```

### 2. Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn plotly scikit-learn kagglehub
```

Atau gunakan versi spesifik untuk menghindari masalah kompatibilitas:

```bash
pip install pandas>=1.3.0 numpy>=1.20.0 matplotlib>=3.4.0 seaborn>=0.11.0 plotly>=5.0.0 scikit-learn>=0.24.0
```

### 3. Jalankan Notebook

Buka salah satu notebook menggunakan Jupyter Notebook atau Google Colab:

- `[v1]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb` (Rekomendasi - versi final)
- `[v0]_Music_Genre_Clustering_using_Spotify_Dataset.ipynb`

---

## 📈 Metodologi

### 1. Exploratory Data Analysis (EDA)
- Analisis statistik deskriptif
- Visualisasi distribusi fitur audio
- Pengecekan missing values dan duplikat

### 2. Data Preprocessing
- Penanganan missing values
- Seleksi fitur numerik untuk clustering
- Standardisasi data menggunakan StandardScaler

### 3. Clustering
- Penentuan jumlah klaster optimal menggunakan:
  - Elbow Method
  - Silhouette Score
- Implementasi K-Means Clustering

### 4. Evaluasi & Visualisasi
- Reduksi dimensi menggunakan PCA
- Visualisasi klaster 2D
- Analisis karakteristik setiap klaster

---

## 📊 Hasil Clustering

Proyek ini menggunakan Elbow Method dan Silhouette Score untuk menentukan jumlah klaster optimal. Berikut contoh karakteristik klaster yang dihasilkan:

| Klaster | Karakteristik |
|---------|---------------|
| 0 | Lagu dengan energy tinggi dan liveness tinggi |
| 1 | Lagu akustik dengan acousticness tinggi dan energy rendah |
| 2 | Lagu energik dengan danceability tinggi |

*Catatan: Jumlah dan karakteristik klaster dapat bervariasi berdasarkan hasil optimasi di notebook. Silakan jalankan notebook untuk melihat hasil lengkap.*

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

---

## 📝 Lisensi

Proyek ini dibuat untuk keperluan tugas praktikum Machine Learning.

---

⭐ Jika repository ini bermanfaat, jangan lupa berikan star!
