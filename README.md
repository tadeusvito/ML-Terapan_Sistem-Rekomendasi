# Laporan Proyek Machine Learning-Terapan - Tadeus Vito Gavra Sitanggang

## Domain Proyek

Industri hiburan, khususnya platform streaming film, telah berkembang pesat dalam beberapa tahun terakhir, seiring dengan meningkatnya kebutuhan masyarakat akan konten film yang beragam dan berkualitas. Salah satu tantangan utama dalam industri ini adalah memberikan rekomendasi film yang relevan dan sesuai dengan preferensi pengguna. Seringkali, platform streaming menggunakan sistem rekomendasi berbasis algoritma untuk membantu pengguna menemukan film yang mereka sukai. Namun, memberikan rekomendasi yang tepat tetap menjadi masalah karena banyaknya variasi preferensi antar pengguna.

Tujuan proyek ini adalah untuk mengembangkan sistem rekomendasi film Netflix yang menggunakan pendekatan **content-based filtering**. Dengan menggunakan algoritma **Cosine Similarity** dan **Euclidean Distance**, diharapkan sistem ini dapat memberikan rekomendasi film yang lebih akurat berdasarkan genre, deskripsi, dan fitur lainnya dari film yang telah ditonton oleh pengguna.

Hasil akhir proyek ini diharapkan dapat meningkatkan pengalaman pengguna dalam menemukan film yang sesuai dengan minat mereka, serta membantu platform dalam meningkatkan retensi pengguna dengan memberikan rekomendasi yang lebih relevan.

## Business Understanding

### Problem Statements
- Bagaimana model rekomendasi berbasis konten dapat membantu pengguna Netflix menemukan film yang relevan dan sesuai dengan preferensi mereka?
- Bagaimana faktor-faktor seperti genre, deskripsi, dan metadata lainnya mempengaruhi kemampuan sistem dalam merekomendasikan film?

### Goals
- Mengidentifikasi faktor-faktor kunci seperti genre, deskripsi, dan metadata film yang memengaruhi rekomendasi.
- Mengembangkan sistem rekomendasi berbasis konten menggunakan algoritma **Cosine Similarity** dan **Euclidean Distance** untuk memberikan rekomendasi film yang lebih akurat dan sesuai dengan preferensi pengguna.

### Solution Statements
- Menggunakan **Cosine Similarity** untuk mengukur kesamaan antara film berdasarkan genre dan deskripsi, serta memberikan rekomendasi film yang paling mirip dengan film yang telah ditonton oleh pengguna.
- Menggunakan **Euclidean Distance** untuk menghitung jarak antar film berdasarkan fitur-fitur yang relevan, memberikan rekomendasi berdasarkan kedekatannya dengan film yang sudah dipilih pengguna.
- Membangun model rekomendasi dengan **content-based filtering** untuk memastikan rekomendasi yang relevan berdasarkan konten film.
- Mengevaluasi performa model dengan mengukur **Precision at K** untuk memastikan sistem memberikan rekomendasi yang tepat sesuai ekspektasi pengguna.

## Data Understanding

Dataset ini merupakan dataset yang berisi informasi mengenai 8807 sampel film dan acara TV yang tersedia di platform Netflix, yang dirancang untuk mendukung penelitian dalam bidang machine learning. Dataset ini mencakup berbagai fitur penting, seperti judul film, genre, rating, dan deskripsi yang memengaruhi rekomendasi film, yang diambil dari referensi yang ada di Kaggle. Dengan fokus pada kemudahan penggunaan dan efisiensi, dataset ini dirancang untuk memenuhi standar tinggi yang diperlukan dalam analisis dan pengembangan model rekomendasi berbasis konten. Keberadaan dataset ini diharapkan dapat memberikan wawasan yang berharga dalam memahami faktor-faktor yang memengaruhi pilihan film dan membantu dalam pengembangan solusi berbasis machine learning.

Sumber Referensi: [Netflix Movies and TV Shows](https://www.kaggle.com/datasets/rahulvyasm/netflix-movies-and-tv-shows)

### Deskripsi Variable

| Nama Kolom         | Deskripsi                                                                 |
|--------------------|---------------------------------------------------------------------------|
| `show_id`          | ID unik untuk masing-masing film atau acara TV                             |
| `type`             | Jenis konten, apakah itu Film (Movie) atau Acara TV (TV Show)              |
| `title`            | Judul film atau acara TV                                                  |
| `director`         | Nama sutradara atau pembuat acara                                         |
| `cast`             | Nama-nama pemeran utama atau tokoh dalam film atau acara TV                |
| `country`          | Negara asal produksi film atau acara TV                                   |
| `date_added`       | Tanggal ketika konten tersebut ditambahkan ke platform Netflix            |
| `release_year`     | Tahun rilis film atau acara TV                                            |
| `rating`           | Rating yang diberikan untuk film atau acara TV (misalnya, PG-13, TV-MA, dll.)|
| `duration`         | Durasi film atau jumlah musim untuk acara TV                               |
| `listed_in`        | Kategori atau genre konten tersebut, seperti Drama, Aksi, Komedi, dll.     |
| `description`      | Deskripsi singkat mengenai alur cerita atau tema dari film atau acara TV   |

- **Jumlah Baris (Entries)**: 8807 baris data
- **Jumlah Kolom (Columns)**: 12 kolom data

### Missing Value

![Missing Value](https://github.com/user-attachments/assets/df764def-3c86-4a74-aed9-80f440c34f8a)

Pada gambar ini, dapat dilihat bahwa dataset memiliki ukuran yang cukup besar, yaitu 8807 entri. Untuk mengatasi masalah nilai yang hilang, baris yang mengandung nilai yang hilang pada kolom-kolom tertentu telah dihapus. Penghapusan baris ini tidak memengaruhi kualitas analisis secara signifikan, karena kehilangan data tersebut tidak berpengaruh besar terhadap representativitas dataset secara keseluruhan. Dengan demikian, dataset yang tersisa tetap dapat digunakan untuk analisis lebih lanjut.

### Data Duplicate

![Data Duplicate](https://github.com/user-attachments/assets/2f99a72b-ba4b-4a81-9cc1-c634f775673b)

Pada hasil output di atas menunjukkan bahwa tidak ada data yang memiliki isi duplikat sama dengan yang lainnya. Hal ini menandakan bahwa dataset yang digunakan telah bersih dari entri yang berulang, yang dapat mempengaruhi keakuratan model.

## Exploratory Data Analysis

### Univariate Analysis

#### Rating

![Rating Distribution](https://github.com/user-attachments/assets/4afccf8c-2c95-4d37-b414-57cef61fcc44)

**Insight:**

- **Rating PG dan TV-14**: Memiliki frekuensi tertinggi, menunjukkan popularitas yang signifikan.
- **Rating TV-MA**: Cukup tinggi, menandakan minat pada konten dewasa.
- **Rating R**: Menunjukkan frekuensi yang lebih rendah dibandingkan PG dan TV-14, tetapi masih relevan.
- **Rating lainnya (TV-PG, TV-Y, dll.)**: Memiliki frekuensi yang jauh lebih rendah, menunjukkan kurangnya popularitas.
- **Distribusi**: Terdapat puncak yang jelas pada beberapa rating, menunjukkan preferensi pemirsa yang kuat terhadap kategori tertentu.

#### Genre

![Genre Distribution](https://github.com/user-attachments/assets/1bbfeef2-e268-4f6f-9cbb-6b79ee10d7ce)

**Insight:**

1. **Dominasi Drama Internasional**: Genre "Dramas, International Movies" mendominasi dengan jumlah film tertinggi, mencapai lebih dari 350 entri. Ini menunjukkan bahwa film drama internasional sangat diminati oleh penonton.
2. **Minat pada Dokumenter**: Genre dokumenter juga menunjukkan jumlah yang signifikan, dengan lebih dari 300 film. Ini mencerminkan ketertarikan penonton terhadap konten yang informatif dan berbasis fakta.
3. **Daya Tarik Stand-Up Comedy**: Genre "Stand-Up Comedy" memiliki jumlah film yang cukup tinggi, menunjukkan bahwa hiburan komedi, terutama dalam format stand-up, sangat populer di kalangan penonton.
4. **Keseimbangan Genre Keluarga**: Genre "Children & Family Movies" dan "Kids' TV" menunjukkan bahwa film dan program untuk anak-anak dan keluarga memiliki pangsa pasar yang besar, menandakan pentingnya konten yang ramah keluarga.
5. **Variasi dalam Genre**: Terdapat variasi dalam genre yang ditampilkan, termasuk komedi dan film independen, menunjukkan keberagaman dalam pilihan film yang tersedia untuk penonton.

#### Tahun Rilis

![image](https://github.com/user-attachments/assets/f934b67e-1d9f-4fc5-9942-ae7f8a32d2d6)

**Insight:**

- **Peningkatan Drastis**: Terjadi lonjakan signifikan dalam jumlah film yang dirilis mulai tahun 2000-an, menunjukkan pertumbuhan industri film yang pesat.
- **Dominasi Tahun 2020**: Tahun 2020 mencatat jumlah film tertinggi, mungkin dipengaruhi oleh platform streaming dan produksi yang meningkat.
- **Stabilitas Sebelum 2000**: Sebelum tahun 2000, jumlah film yang dirilis relatif rendah dan stabil, menunjukkan pertumbuhan industri yang lambat.
- **Tren Modern**: Munculnya teknologi dan platform baru berkontribusi pada peningkatan jumlah film yang dirilis dalam dua dekade terakhir.

#### Durasi Film

![image](https://github.com/user-attachments/assets/e3a242d1-df35-45ae-8f8d-b4b19c748b3d)

**Insight:**

1. **Puncak Durasi**: Mayoritas film memiliki durasi antara 80 hingga 120 menit, dengan puncak tertinggi di sekitar 100 menit. Ini menunjukkan bahwa durasi ini adalah yang paling disukai oleh pembuat film dan penonton.
2. **Frekuensi Tinggi**: Terdapat frekuensi tinggi untuk film dengan durasi di bawah 100 menit, menunjukkan bahwa film pendek lebih umum dan mungkin lebih menarik bagi penonton yang mencari pengalaman menonton yang lebih singkat.
3. **Penurunan Drastis**: Setelah 150 menit, frekuensi film menurun secara signifikan, menunjukkan bahwa film dengan durasi lebih panjang jarang diproduksi atau kurang diminati.
4. **Distribusi Normal**: Kurva distribusi menunjukkan pola yang mendekati distribusi normal, dengan sebagian besar film berkumpul di sekitar durasi rata-rata, dan sedikit film yang memiliki durasi ekstrem.

## Data Preparation
### Handling Missing Value

```python
netflix_clean = netflix.dropna()
```
Karena ukuran dataset ini cukup besar (8807 entri), masalah nilai yang hilang dapat diatasi dengan menghapus baris yang mengandung nilai tersebut tanpa memengaruhi kualitas analisis secara signifikan. Menghapus baris dengan nilai yang hilang di kolom-kolom tersebut adalah solusi yang tepat, karena penghapusan ini tidak akan mengurangi data secara signifikan dan dataset akan tetap representatif untuk analisis berikutnya.

### Feature Engineering

Kolom-kolom yang relevan dipilih untuk digunakan dalam sistem rekomendasi film. Kolom yang dipilih terdiri dari show_id, yang merupakan ID unik untuk setiap film atau acara TV, title, yang berisi judul film atau acara, dan listed_in, yang mencakup genre atau kategori film tersebut. Setiap film atau acara bisa memiliki lebih dari satu genre. Dengan memilih kolom-kolom ini, dataset menjadi lebih terfokus pada elemen-elemen utama yang diperlukan untuk menghasilkan rekomendasi yang akurat, terutama berdasarkan genre yang sangat penting dalam menentukan kesamaan antar film atau acara TV.
```python
rec_netflix = netflix_clean[['show_id', 'title', 'listed_in']]
rec_netflix.head()
```
![image](https://github.com/user-attachments/assets/485a55ee-d121-4bf0-a122-bc92ee40cc84)

Setelah itu dilakukan pembersihan dan standarisasi genre dalam kolom **listed_in**, langkah selanjutnya adalah memastikan konsistensi format genre untuk memudahkan pemrosesan data. Proses ini penting karena dalam analisis teks atau perhitungan kesamaan, ketidakkonsistenan dalam penulisan genre (misalnya "Sci-Fi" menjadi "scifi" ) dapat mempengaruhi hasil pemrosesan dan perhitungan kesamaan antar item. Oleh karena itu, genre dengan format atau penulisan yang berbeda akan disesuaikan agar memiliki format yang lebih seragam, sehingga analisis selanjutnya menjadi lebih akurat dan konsisten.
```python
rec_netflix.loc[rec_netflix['listed_in'].str.contains('Sci-Fi', na=False), 'listed_in'] = rec_netflix['listed_in'].str.replace('Sci-Fi', 'scifi')
```

Selanjutnya, kolom **show_id**, **title**, dan **listed_in** diubah menjadi list untuk memudahkan pemrosesan data menggunakan TfidfVectorizer dari scikit-learn. Dalam konteks ini, TfidfVectorizer membutuhkan input dalam bentuk list string, di mana setiap string mewakili genre atau kategori film secara individual. Proses ini memastikan bahwa setiap nilai dalam kolom-kolom tersebut dapat diproses secara efisien untuk analisis selanjutnya, terutama dalam perhitungan kesamaan antar item berdasarkan genre.
```python
netflix_show_id = rec_netflix['show_id'].tolist()

netflix_title = rec_netflix['title'].tolist()

netflix_genre = rec_netflix['listed_in'].tolist()
```

### One Hot Encoding
```python
# Membuat daftar genre unik
genre_list = []

for index in netflix_new.index:
    temp = netflix_new['listed_in'][index].split(',')
    for i in temp:
        if i.strip() not in genre_list:  # Tambahkan pengecekan agar genre tidak duplikat
            genre_list.append(i.strip())

# Membuat DataFrame untuk one-hot encoding
onehot_df = pd.DataFrame(0, index=netflix_new.index, columns=genre_list)

# Mengisi nilai 1 untuk genre yang sesuai
for index in netflix_new.index:
    temp = netflix_new['listed_in'][index].split(',')
    for i in temp:
        onehot_df.loc[index, i.strip()] = 1  # Menambahkan strip untuk menghilangkan spasi yang tidak diperlukan

# Menggabungkan DataFrame hasil one-hot encoding dengan DataFrame asli
netflix_new = pd.concat([netflix_new, onehot_df], axis=1)

# Menampilkan hasil
netflix_new.head()
```
Selanjutnya melalui proses one-hot encoding, di mana setiap kategori atau genre yang ada di kolom listed_in dikodekan dalam bentuk biner (0 atau 1). Setiap baris mewakili entri dalam dataset, seperti film atau acara TV, dan setiap kolom yang mewakili genre atau kategori menunjukkan apakah genre tersebut termasuk dalam entri tersebut. Proses ini mempermudah analisis data, seperti perhitungan kesamaan atau pengelompokan, dengan mengubah kategori menjadi format yang lebih mudah diproses secara matematis.
![image](https://github.com/user-attachments/assets/232cff95-4fa0-47aa-a581-1180d9386541)

### TD-IDF Vectorizer
```python
from sklearn.feature_extraction.text import TfidfVectorizer

# Inisialisasi TfidfVectorizer
tfid = TfidfVectorizer()

# Melakukan perhitungan idf pada data genre
tfid.fit(netflix_new['listed_in'])

# Mapping array dari fitur index integer ke fitur nama
# Use get_feature_names_out() instead of get_feature_names()
tfid.get_feature_names_out()
```
Kode di atas menunjukkan penggunaan **TfidfVectorizer** dari pustaka `sklearn` untuk menghitung nilai **TF-IDF** pada data genre film yang terdapat dalam kolom **listed_in**. Dengan menginisialisasi objek `TfidfVectorizer`, kode ini menghitung **IDF (Inverse Document Frequency)** dari setiap genre dalam dataset, yang kemudian dikonversi menjadi vektor numerik. Fungsi `get_feature_names_out()` digunakan untuk mendapatkan daftar genre yang telah diproses, seperti **'action'**, **'comedy'**, **'documentaries'**, dan lainnya. Proses ini memungkinkan data teks diubah menjadi format numerik yang dapat digunakan untuk analisis lebih lanjut, seperti perhitungan kesamaan antar film berdasarkan genre.

## Modeling
### Cosine Similarity
```python
from sklearn.metrics.pairwise import cosine_similarity

# Menghitung cosine similarity pada matrix tf-idf
cosine_sim = cosine_similarity(tfid_matrix)
cosine_sim
```
Tahap di atas menunjukkan perhitungan **cosine similarity** menggunakan matriks **TF-IDF** yang dihitung sebelumnya. **Cosine similarity** adalah ukuran kesamaan antara dua vektor teks berdasarkan sudut antar vektor tersebut. Hasil dari `cosine_similarity(tfid_matrix)` menghasilkan sebuah matriks yang menunjukkan tingkat kesamaan antara setiap pasangan item (misalnya, film atau acara TV) berdasarkan genre yang ada.

**Langkah-langkah yang dilakukan:**
1. **Perhitungan Cosine Similarity**:
   Dengan menggunakan `cosine_similarity()` dari `sklearn.metrics.pairwise`, kesamaan antara setiap film dihitung berdasarkan matriks **TF-IDF** (`tfid_matrix`). Hasilnya adalah sebuah matriks berukuran (5185, 5185) yang menggambarkan seberapa mirip setiap film dengan yang lainnya.
2. **Membuat DataFrame**:
   Matriks cosine similarity kemudian diubah menjadi DataFrame dengan menggunakan `pd.DataFrame()`, di mana baris dan kolomnya berisi **title** dari film atau acara TV. Hal ini memudahkan untuk melihat kesamaan antara setiap item dengan lebih jelas.
3. **Melihat Matriks Cosine Similarity**:
   Matriks kesamaan ini ditampilkan sebagian dengan `sample()`, sehingga dapat dilihat seberapa mirip setiap judul film dengan judul lainnya berdasarkan genre.

**Hasil Rekomendasi Cosine Similarity**
![image](https://github.com/user-attachments/assets/91a44b95-7777-425b-83c8-d02ba5c07179)

**List 10 Film yang direkomendasikan dengan Cosine Similarity dari Film "Time to Dance":**
![image](https://github.com/user-attachments/assets/4d3e04ef-ef98-4bf2-b2a5-6c0884212bad)

### Euclidean Distance
```python
from sklearn.metrics.pairwise import euclidean_distances

euclidean_sim = euclidean_distances(tfid_matrix)
euclidean_sim
```
Tahap di atas menunjukkan perhitungan **Euclidean distance** menggunakan matriks **TF-IDF** yang dihitung sebelumnya. **Euclidean distance** adalah ukuran jarak antara dua vektor dalam ruang multidimensi, yang dihitung berdasarkan perbedaan nilai-nilai dalam vektor tersebut. Hasil dari `euclidean_distances(tfid_matrix)` menghasilkan sebuah matriks yang menunjukkan seberapa jauh jarak antara setiap pasangan item (misalnya, film atau acara TV) berdasarkan genre yang ada.

**Langkah-langkah yang dilakukan:**
1. **Perhitungan Euclidean Distance**:
   Dengan menggunakan `euclidean_distances()` dari `sklearn.metrics.pairwise`, jarak antara setiap film dihitung berdasarkan matriks **TF-IDF** (`tfid_matrix`). Hasilnya adalah sebuah matriks berukuran (5185, 5185) yang menggambarkan jarak antara setiap film dengan film lainnya.
2. **Membuat DataFrame**:
   Matriks Euclidean distance kemudian diubah menjadi DataFrame dengan menggunakan `pd.DataFrame()`, di mana baris dan kolomnya berisi **title** dari film atau acara TV. Hal ini memudahkan untuk melihat jarak antara setiap item dengan lebih jelas.
3. **Melihat Matriks Euclidean Distance**:
   Matriks jarak ini ditampilkan sebagian dengan `sample()`, sehingga dapat dilihat seberapa jauh jarak antar judul film berdasarkan genre.

**Hasil Rekomendasi Euclidean Distance**
![image](https://github.com/user-attachments/assets/860be56a-c185-4a99-b8cb-564c47676eae)

**List 10 Film yang direkomendasikan dengan Euclidean Distance dari Film "Time to Dance":**
![image](https://github.com/user-attachments/assets/734a30b8-ccb3-4616-a9c4-99acdaf92902)

## Evaluation
### Evaluasi Precision at K (P@K)

Pada proyek ini, metrik **Precision at K (P@K)** digunakan untuk mengevaluasi kualitas rekomendasi yang dihasilkan oleh dua metode: **Cosine Similarity** dan **Euclidean Distance**. Precision mengukur seberapa banyak rekomendasi yang relevan ada di antara K rekomendasi teratas yang diberikan oleh sistem.

#### Langkah-langkah yang dilakukan:

1. **Pengambilan Data Rekomendasi**:
   - **`relevant_netflix`**: Data relevan dipilih dari dataset berdasarkan genre film yang termasuk dalam kategori "Drama" atau "Romantic Movies".
   - **`cosine_recommended`**: Menggunakan metode **Cosine Similarity**, rekomendasi film diperoleh berdasarkan genre dan deskripsi film yang relevan. Sebagai contoh, film "Time to Dance" dipilih untuk pengujian.
   - **`euclidean_recommended`**: Dengan menggunakan **Euclidean Distance**, daftar rekomendasi diperoleh berdasarkan kedekatannya dengan film "Everyday I Love You".

2. **Perhitungan Precision at K (P@K)**:
   Fungsi `precision_at_k()` menghitung seberapa banyak film yang relevan ada dalam 10 rekomendasi teratas yang diberikan oleh sistem. Fungsi ini:
   - Menerima parameter `recommended` (daftar film yang direkomendasikan), `actual` (daftar film yang relevan menurut preferensi pengguna), dan `k` (jumlah rekomendasi yang dievaluasi, dalam hal ini k=10).
   - Menghitung jumlah film yang relevan di antara 10 rekomendasi teratas dan membaginya dengan jumlah rekomendasi yang diuji (K=10).

3. **Menampilkan Hasil Precision**:
   Setelah melakukan perhitungan, hasil Precision untuk kedua metode, yaitu **Cosine Similarity** dan **Euclidean Distance**, ditampilkan. Hasil yang diperoleh adalah:
   - **Precision at K untuk Cosine Similarity**: 1.00
   - **Precision at K untuk Euclidean Distance**: 1.00

![image](https://github.com/user-attachments/assets/06f53021-0478-413a-92fd-90f4c195b83b)

Hasil ini menunjukkan bahwa kedua metode berhasil memberikan 10 rekomendasi teratas yang sepenuhnya relevan dengan preferensi pengguna, yang menandakan bahwa sistem rekomendasi bekerja dengan sangat baik dalam menghasilkan rekomendasi yang sesuai dengan harapan pengguna.

#### Penjelasan Hasil:
- **Cosine Similarity**: Rekomendasi yang diberikan dengan menggunakan Cosine Similarity, seperti film "Raja Hindustani" dan "No Other Woman", semuanya relevan dengan kategori yang dicari oleh pengguna.
- **Euclidean Distance**: Rekomendasi yang diberikan dengan menggunakan Euclidean Distance, seperti "A Second Chance" dan "The Mistress", juga relevan dan sesuai dengan film yang dipilih oleh pengguna.

Kesimpulannya, kedua metode **Cosine Similarity** dan **Euclidean Distance** berhasil memberikan rekomendasi yang relevan dan akurat, yang diukur dengan nilai Precision sebesar 1.00.

## Kesimpulan

Proyek ini berhasil mengembangkan sistem rekomendasi film berbasis **Content-Based Filtering** menggunakan **Cosine Similarity** dan **Euclidean Distance**. Kedua metode menghasilkan rekomendasi yang sangat relevan, dengan nilai **Precision at K (P@K)** mencapai 1.00, menunjukkan akurasi tinggi dalam 10 rekomendasi teratas.

Hasil ini menunjukkan bahwa pendekatan berbasis konten dapat efektif dalam memberikan rekomendasi film yang sesuai dengan preferensi pengguna, meningkatkan pengalaman menonton, serta berpotensi meningkatkan retensi pengguna pada platform streaming seperti Netflix.

## Referensi
1. [Netflix Movies and TV Shows](https://www.kaggle.com/datasets/rahulvyasm/netflix-movies-and-tv-shows)
2. [Dicoding Indonesia](https://www.dicoding.com)

