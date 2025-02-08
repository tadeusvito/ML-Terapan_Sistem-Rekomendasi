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
- Menggunakan **Cosine Similarity** untuk mengukur kesamaan antara film berdasarkan genre dan deskripsi, dan memberikan rekomendasi film yang paling mirip dengan film yang telah ditonton oleh pengguna.
- Menggunakan **Euclidean Distance** untuk menghitung jarak antar film berdasarkan fitur-fitur yang relevan, memberikan rekomendasi berdasarkan kedekatannya dengan film yang sudah dipilih pengguna.
- Membangun model rekomendasi dengan **content-based filtering** untuk memastikan rekomendasi yang relevan berdasarkan konten film.
- Mengevaluasi performa model dengan mengukur **Precision at K** untuk memastikan sistem memberikan rekomendasi yang tepat sesuai ekspektasi pengguna.

## Data Understanding
Dataset ini merupakan dataset yang berisi informasi mengenai 8807 sampel film dan acara TV yang tersedia di platform Netflix, yang dirancang untuk mendukung penelitian dalam bidang machine learning. Dataset ini mencakup berbagai fitur penting, seperti judul film, genre, rating, dan deskripsi yang memengaruhi rekomendasi film, yang diambil dari referensi yang ada di Kaggle. Dengan fokus pada kemudahan penggunaan dan efisiensi, dataset ini dirancang untuk memenuhi standar tinggi yang diperlukan dalam analisis dan pengembangan model rekomendasi berbasis konten. Keberadaan dataset ini diharapkan dapat memberikan wawasan yang berharga dalam memahami faktor-faktor yang memengaruhi pilihan film dan membantu dalam pengembangan solusi berbasis machine learning.

Sumber Referensi: [Netflix Movies and TV Shows](https://www.kaggle.com/datasets/rahulvyasm/netflix-movies-and-tv-shows)

### Deskripsi Variable
|      Nama Kolom       |                         Deskripsi                           |  
|-----------------------|------------------------------------------------------------|  
| show_id               | ID unik untuk masing-masing film atau acara TV              |  
| type                  | Jenis konten, apakah itu Film (Movie) atau Acara TV (TV Show)|  
| title                 | Judul film atau acara TV                                   |  
| director             | Nama sutradara atau pembuat acara                          |  
| cast                  | Nama-nama pemeran utama atau tokoh dalam film atau acara TV  |  
| country               | Negara asal produksi film atau acara TV                    |  
| date_added            | Tanggal ketika konten tersebut ditambahkan ke platform Netflix|  
| release_year          | Tahun rilis film atau acara TV tersebut                     |  
| rating                | Rating yang diberikan untuk film atau acara TV tersebut (misalnya, PG-13, TV-MA, dll.)|  
| duration              | Durasi film atau jumlah musim untuk acara TV                |  
| listed_in             | Kategori atau genre konten tersebut, seperti Drama, Aksi, Komedi, dll.|  
| description           | Deskripsi singkat mengenai alur cerita atau tema dari film atau acara TV|

- **Jumlah Baris (Entries)**: 8807 baris data, terdapat 8807 entri atau record yang tercatat dalam dataset ini.  
- **Jumlah Kolom (Columns)**: 12 kolom data, yang mencakup berbagai atribut terkait film dan acara TV yang tercatat dalam dataset.

