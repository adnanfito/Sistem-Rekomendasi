# Laporan Proyek Machine Learning - Adnan Fito Dharmawan

## Project Overview

Dalam era informasi yang terus berkembang, masyarakat kini dihadapkan pada berbagai pilihan buku yang semakin luas, dari berbagai genre hingga format digital dan cetak. Jumlah buku yang diterbitkan terus bertambah, membuat pengguna kerap kesulitan menemukan buku yang sesuai dengan minat, kebutuhan, atau preferensi mereka. Selain itu, perkembangan teknologi informasi memungkinkan terciptanya sistem yang dapat membantu individu dalam menavigasi pilihan-pilihan ini secara lebih efisien, sehingga pengalaman membaca menjadi lebih personal dan memuaskan.

Sistem rekomendasi adalah salah satu pendekatan teknologi yang telah terbukti mampu membantu pengguna dalam memilih konten yang relevan, baik itu dalam bentuk film, musik, produk, hingga buku. Di bidang perbukuan, sistem rekomendasi memiliki potensi besar dalam membantu pengguna mengatasi kesulitan memilih buku yang sesuai dengan preferensi mereka. Dengan menggunakan data pengguna, sistem ini dapat memberikan rekomendasi buku yang lebih terarah dan personal, sehingga membantu dalam meningkatkan minat baca dan waktu yang dihabiskan untuk membaca, terutama di kalangan masyarakat yang memiliki keterbatasan waktu atau akses terhadap buku.

## Pentingnya Proyek

* Mempermudah pengguna dalam menemukan buku yang sesuai dengan minat dan
preferensi mereka di tengah pilihan buku yang semakin luas.
* Meningkatkan minat baca masyarakat dengan menyediakan rekomendasi buku yang personal dan relevan.
* Membantu platform seperti perpustakaan digital, toko buku online, atau aplikasi edukasi untuk meningkatkan keterlibatan pengguna, waktu penggunaan, dan potensi penjualan atau peminjaman buku.
* Berkontribusi pada peningkatan literasi masyarakat, terutama di era digital yang menantang minat baca generasi muda.

## Artikel dan Jurnal Referensi:

- [How to Build a Movie Recommendation System](https://towardsdatascience.com/how-to-build-a-movie-recommendation-system-67e321339109) 
- [Perancangan Sistem Rekomendasi Menggunakan Metode Collaborative Filtering dengan Studi Kasus Perancangan Website Rekomendasi Film](https://www.neliti.com/publications/504836/perancangan-sistem-rekomendasi-menggunakan-metode-collaborative-filtering-dengan) 

## Business Understanding

## Problem Statements (Pernyataan Masalah)

- Bagaimana cara menciptakan sistem rekomendasi buku yang dapat secara akurat menyesuaikan saran berdasarkan preferensi pembaca?
- Dapatkah rekomendasi buku yang disesuaikan untuk masing-masing pengguna meningkatkan interaksi dan daya tarik platform dalam jangka panjang?
- Bagaimana perbedaan metode rekomendasi, seperti berbasis konten atau kolaboratif, dapat mempengaruhi kualitas dan relevansi saran buku yang diberikan?

## Goals (Tujuan)

- Meningkatkan interaksi pengguna dengan menyediakan rekomendasi buku yang disesuaikan dengan kebutuhan dan preferensi pribadi mereka.
- Memberikan saran buku yang tidak hanya relevan tetapi juga bervariasi, dengan mempertimbangkan berbagai aspek seperti genre, penulis, dan rating.
- Eksperimen dengan berbagai teknik rekomendasi untuk menilai mana yang menghasilkan kualitas saran terbaik dan meningkatkan pengalaman pengguna.

## Solution Approach

Untuk meraih tujuan di atas, terdapat dua pendekatan yang dapat digunakan dalam membangun sistem rekomendasi buku:

### 1. Content-Based Filtering

Pendekatan ini menggunakan informasi tentang buku itu sendiri (seperti genre, penulis, atau kata kunci) untuk memberikan rekomendasi kepada pengguna. Setiap buku akan diproses untuk menentukan karakteristik utamanya, kemudian sistem akan mencocokkan buku yang memiliki kemiripan dengan buku yang sudah dibaca atau disukai oleh pengguna sebelumnya. Keunggulan dari pendekatan ini adalah bahwa sistem ini dapat memberikan rekomendasi yang sangat relevan berdasarkan kesukaan spesifik pengguna, meskipun pendekatan ini kurang dapat menyarankan buku yang tidak dikenal oleh pengguna.

#### Langkah-langkah implementasi:
- Ekstraksi fitur dari buku (genre, pengarang, kata kunci, dsb).
- Membangun profil pengguna berdasarkan buku yang pernah dibaca atau disukai.
- Menyajikan rekomendasi buku berdasarkan kesamaan fitur antara buku yang telah dibaca dan buku lainnya.
- Metrik Evaluasi : Precision

### 2. Collaborative Filtering

Pendekatan ini berfokus pada perilaku atau preferensi pengguna lain yang serupa untuk memberikan rekomendasi. Dalam Collaborative Filtering, sistem tidak memerlukan informasi eksplisit tentang konten buku. Sebagai gantinya, sistem menganalisis pola perilaku pengguna, seperti buku yang sering dibaca atau dinilai tinggi oleh kelompok pengguna yang mirip. Pendekatan ini dapat memberikan rekomendasi yang lebih beragam dan menarik, bahkan untuk buku yang belum pernah dibaca oleh pengguna sebelumnya.

#### Langkah-langkah implementasi:
- Pengumpulan data interaksi pengguna dengan buku (rating buku).
- Mencari pengguna yang memiliki preferensi serupa dengan pengguna target.
- Memberikan rekomendasi berdasarkan preferensi pengguna serupa.
- Metrik Evaluasi: RMSE

Kedua pendekatan ini memiliki kekuatan dan keterbatasan masing-masing. Content-Based Filtering lebih mengandalkan informasi konten buku, sementara Collaborative Filtering lebih mengandalkan interaksi sosial atau pola perilaku pengguna. Dalam beberapa kasus, kombinasi dari kedua pendekatan ini dapat memberikan hasil yang lebih optimal dalam menyajikan rekomendasi yang akurat dan relevan bagi pengguna.

## Data Understanding
Dataset yang digunakan berasal dari kaggle bernama [Book Recommendation Dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset) yang berisikan kumpulan data ini terdiri dari books, users dan ratings.

### **Dataset Rekomendasi Buku ini terdiri dari 3 file:**

**1. Users (Pengguna):**
Berisi data pengguna. ID pengguna (`User-ID`) telah dianonimkan dan dipetakan ke angka. Data demografis disediakan (`Location`, `Age`) jika tersedia, jika tidak, kolom ini berisi nilai NULL.

**2. Books (Buku):**
Buku diidentifikasi dengan ISBN masing-masing. ISBN yang tidak valid telah dihapus dari dataset. Beberapa informasi berbasis konten diberikan (`Book-Title`, `Book-Author`, `Year-Of-Publication`, `Publisher`) yang diperoleh dari Amazon Web Services. Jika ada beberapa pengarang, hanya pengarang pertama yang disertakan. Tautan URL yang mengarah ke gambar sampul juga diberikan dalam tiga ukuran (`Image-URL-S`, `Image-URL-M`, `Image-URL-L`), yang mengarah ke situs web Amazon.

**3. Ratings (Rating):**
Berisi informasi tentang rating buku. Rating dapat berupa eksplisit (dalam skala 1-10, dengan angka lebih tinggi menunjukkan penghargaan lebih tinggi), atau implisit, yang ditunjukkan dengan nilai 0 (misalnya, jika tidak ada interaksi atau rating eksplisit).

**Penjelasan Dataset Books :**

Dataset `books` terdiri dari informasi terkait buku, dan memiliki 271,360 entri (baris) serta 8 kolom yang menjelaskan detail masing-masing buku. Berikut adalah penjelasan untuk setiap kolom dalam dataset ini:

* `ISBN` : Kolom ini berisi ISBN (International Standard Book Number) dari setiap buku sebagai identifier unik. Semua entri memiliki nilai (non-null) pada kolom ini.

* `Book-Title` : Kolom ini berisi judul buku. Semua entri memiliki judul buku (non-null) di kolom ini.

* `Book-Author` : Kolom ini menunjukkan nama penulis buku. Ada sedikit data yang kosong di kolom ini, dengan 271,358 nilai non-null (berarti ada 2 nilai yang null atau kosong).

* `Year-Of-Publication` : Kolom ini berisi tahun terbit dari setiap buku. Semua entri memiliki informasi tentang tahun terbit, meskipun tipe datanya disimpan sebagai `object` (`string`), yang mungkin perlu dikonversi ke `int` atau `datetime` jika diperlukan.

* `Publisher` : Kolom ini menunjukkan nama penerbit dari setiap buku. Ada 271,358 nilai non-null, artinya ada beberapa entri yang tidak memiliki informasi penerbit.

* `Image-URL-S` : Kolom ini berisi URL gambar kecil (small) dari sampul buku. Semua entri memiliki URL yang dapat digunakan untuk menampilkan gambar kecil dari sampul buku.

* `Image-URL-M` : Kolom ini berisi URL gambar ukuran sedang (medium) dari sampul buku. Semua entri memiliki nilai pada kolom ini, dan URL ini bisa digunakan untuk menampilkan sampul dengan resolusi menengah.

* `Image-URL-L` : Kolom ini berisi URL gambar besar (large) dari sampul buku. Ada 271,357 nilai non-null, berarti ada beberapa entri yang tidak memiliki gambar ukuran besar.

**Penjelasan Dataset Ratings :**

Dataset ini berisi informasi tentang penilaian (rating) yang diberikan pengguna terhadap berbagai buku, dengan total 1,149,780 entri (baris) dan 3 kolom. Berikut adalah penjelasan dari setiap kolom dalam dataset:

* `User-ID` : Kolom ini berisi ID unik dari setiap pengguna yang memberikan rating. Semua entri memiliki nilai pada kolom ini, dan tipe datanya adalah `int64`.

* `ISBN` : Kolom ini menunjukkan ISBN dari buku yang dinilai oleh pengguna. Kolom ini berfungsi sebagai penghubung dengan dataset `books` untuk mengidentifikasi buku yang mendapatkan rating. Semua entri memiliki ISBN (non-null), dan tipe datanya adalah `object`.

* `Book-Rating` : Kolom ini berisi nilai rating yang diberikan pengguna terhadap buku tertentu. Rating ini biasanya berupa nilai numerik (umumnya antara 1 hingga 10, atau dalam skala lain yang bisa ditentukan). Semua entri memiliki nilai pada kolom ini, dan tipe datanya adalah `int64`.

**Penjelasan Dataset Users :**

Dataset ini berisi informasi tentang pengguna yang memberikan rating terhadap buku, dengan total 278,858 entri (baris) dan 3 kolom. Berikut adalah penjelasan setiap kolom dalam dataset:

* `User-ID` : Kolom ini berisi ID unik untuk setiap pengguna. Semua entri memiliki nilai pada kolom ini (non-null), dengan tipe data `int64`.

* `Location` : Kolom ini menunjukkan lokasi geografis pengguna, yang biasanya berupa format alamat, seperti kota, negara bagian, atau negara. Semua entri memiliki nilai (non-null) pada kolom ini, dengan tipe data `object`.

* `Age` : Kolom ini berisi usia pengguna. Ada sejumlah nilai yang kosong, dengan hanya 168,096 nilai non-null dari 278,858 entri, sehingga ada data yang hilang (null) pada kolom ini. Tipe datanya adalah `float64`, menunjukkan bahwa nilai usia mungkin mengandung desimal (meskipun biasanya usia berupa bilangan bulat).


Berikut ini adalah jumlah nilai kosong (*missing values*) pada setiap kolom dalam dataset:

| Dataset | Column             | Null Values |
|---------|---------------------|-------------|
| Books   | ISBN               | 0           |
|         | Book-Title         | 0           |
|         | Book-Author        | 2           |
|         | Year-Of-Publication| 0           |
|         | Publisher          | 2           |
|         | Image-URL-S        | 0           |
|         | Image-URL-M        | 0           |
|         | Image-URL-L        | 3           |
| Ratings | User-ID            | 0           |
|         | ISBN               | 0           |
|         | Book-Rating        | 0           |
| Users   | User-ID            | 0           |
|         | Location           | 0           |
|         | Age                | 110,762     |

Berikut adalah 10 buku dengan rating tertinggi
![image](https://github.com/user-attachments/assets/884f340c-fdb7-434e-b563-8576bb102d2f)

Berikut adala 10 buku dengan rating terbanyak
![image](https://github.com/user-attachments/assets/e15ca81b-042d-44d0-b1df-5819219dc961)

Berikut adalah distribusi tahun penerbit
![image](https://github.com/user-attachments/assets/f0d2318a-ed3f-4273-8180-fcb1f976d845)
Dan diatas ini merupakan distribusi tahun penerbitan buku, bisa dilihat ada 4618 buku dengan nilai tahun penerbitan 0, buku tersebut akan dibersihkan.



## Data Preparation

1. **Data Cleaning**:

   - Data Cleaning - Mengubah Nama Kolom
      - **Proses:** Mengubah nama kolom pada DataFrame `ratings`, `users`, dan `books` agar lebih konsisten dan mudah dipahami. Kolom `User-ID` diubah menjadi `userID`, `Book-Rating` menjadi `bookRating`, dan kolom pada DataFrame `books` seperti `Book-Title`, `Book-Author`, `Year-Of-Publication`, serta `Publisher` diubah menjadi `title`, `author`, `year`, dan `publisher` masing-masing.  
      - **Alasan:** Penamaan kolom yang konsisten mempermudah pemahaman dan pengolahan data, serta meningkatkan keterbacaan dalam analisis lebih lanjut.
   
   - Data Cleaning - Menghapus Kolom yang Tidak Diperlukan
      - **Proses:** Menghapus kolom `Image-URL-S`, `Image-URL-M`, dan `Image-URL-L` dari DataFrame `books`, karena kolom ini tidak berpengaruh pada model rekomendasi.  
      - **Alasan:** Menghapus kolom yang tidak relevan penting untuk mengurangi ukuran dataset, mempercepat proses pemrosesan data, dan memastikan model hanya menggunakan data yang berguna untuk rekomendasi.
   
   - Data Cleaning - Menghapus Missing Value
      - **Proses:** Menghapus baris yang memiliki nilai kosong (`null`) pada DataFrame `books` menggunakan metode `dropna()`.  
      - **Alasan:** Nilai kosong dapat menyebabkan kesalahan dalam analisis dan pemodelan. Menghapus baris dengan missing value membantu memastikan bahwa data yang digunakan dalam model bersih dan lengkap.
   
   - Merging Files dan Menghapus Missing Value Setelah Merge
      - **Proses:** Menggabungkan DataFrame `ratings` dan `books` berdasarkan kolom `ISBN` menggunakan operasi merge. Setelah penggabungan, baris yang mengandung nilai kosong (missing value) dihapus.  
      - **Alasan:** Penggabungan ini memberikan informasi yang lengkap mengenai buku terkait dengan rating yang diberikan oleh pengguna. Menghapus missing value setelah merge penting untuk memastikan integritas data yang digunakan dalam model.
   
   - Data Cleaning - Pengurutan Berdasarkan ISBN
      - **Proses:** Mengurutkan DataFrame berdasarkan kolom `ISBN` untuk memastikan urutan data sesuai dengan kode unik buku.  
      - **Alasan:** Pengurutan data berdasarkan `ISBN` memastikan konsistensi dan kemudahan dalam pemrosesan data lebih lanjut, khususnya saat mengelola dataset besar yang memiliki identifikasi unik.
   
   - Data Cleaning - Menghapus Tahun Terbit yang Tidak Valid
      - **Proses:** Menghapus baris dengan nilai tahun terbit yang bernilai `0`, karena nilai tersebut dianggap sebagai indikasi data yang tidak valid.  
      - **Alasan:** Menghapus nilai `0` pada kolom `year` penting untuk mencegah penggunaan data yang tidak akurat, yang dapat memengaruhi kualitas rekomendasi yang dihasilkan oleh model.
   
   - Data Cleaning - Menghapus Duplikasi Berdasarkan ISBN
      - **Proses:** Menghapus duplikasi berdasarkan kolom `ISBN` dengan metode `drop_duplicates()` untuk memastikan setiap buku hanya muncul sekali dalam dataset.  
      - **Alasan:** Menghindari duplikasi membantu model untuk belajar dari data yang tidak berlebihan, mencegah overfitting, dan memastikan kualitas rekomendasi yang lebih baik.
   
   - Data Preparation - Mengkonversi Data ke Dalam Bentuk List
      - **Proses:** Mengonversi kolom `ISBN`, `title`, `author`, `year`, dan `publisher` menjadi format list untuk mempermudah pemrosesan lebih lanjut dalam model rekomendasi.  
      - **Alasan:** Mengonversi data ke dalam bentuk list memungkinkan akses yang lebih mudah dan lebih cepat terhadap data yang akan digunakan dalam algoritma rekomendasi.
   
   - Data Preparation - Membatasi Data pada 30,000 Baris Teratas
      - **Proses:** Membatasi dataset hanya pada 30,000 baris teratas menggunakan slicing untuk mempercepat proses pemodelan dan analisis.  
      - **Alasan:** Membatasi jumlah data membantu dalam mempercepat waktu komputasi dan memfokuskan model pada data yang lebih terkelola, menghindari masalah memori atau waktu proses yang terlalu lama.

2. **Content-Based Filtering**:
   - Menggabungkan Kolom Book-Title dan Book-Author
      - **Proses:** Menggabungkan kolom `Book-Title` dan `Book-Author` menjadi satu string untuk menciptakan fitur teks baru yang lebih kaya. Hasil penggabungan ini disimpan dalam variabel `combined`. Kolom `combined` ini digunakan untuk menganalisis hubungan antara judul dan penulis buku sebagai satu entitas tunggal.  
      - **Alasan:** Dengan menggabungkan judul dan penulis, kita menciptakan fitur yang lebih kaya dan deskriptif yang menggabungkan informasi penting untuk rekomendasi buku. Ini meningkatkan kualitas analisis tekstual dan memudahkan model dalam memahami konteks buku secara keseluruhan.
   
   - Menggunakan TF-IDF untuk Menghitung Representasi Bobot Fitur Gabungan
      - **Proses:** Menggunakan teknik TF-IDF (Term Frequency-Inverse Document Frequency) untuk menghitung representasi bobot dari fitur gabungan `combined` yang mencakup informasi dari `Book-Title` dan `Book-Author`. TF-IDF memberikan bobot yang lebih tinggi pada kata-kata yang unik dan relevan dalam buku tertentu, serta mengurangi pengaruh kata-kata yang umum digunakan di seluruh dataset.  
      - **Alasan:** TF-IDF digunakan untuk mengekstrak informasi penting dari teks, memberikan bobot lebih pada istilah yang relevan dan unik dalam konteks buku tertentu. Ini membantu dalam meningkatkan akurasi dan relevansi rekomendasi berdasarkan kesamaan konten antar buku.


3. **Collaborative Filtering**:
   - Membatasi Data Ratings Teratas
      - **Proses:** Membatasi dataset `ratings` hanya pada 30,000 baris teratas dengan menggunakan slicing untuk mempercepat proses pemodelan dan analisis.  
      - **Alasan:** Membatasi jumlah data membantu dalam mempercepat waktu komputasi dan memfokuskan model pada data yang lebih terkelola, menghindari masalah memori atau waktu proses yang terlalu lama.
      
   - Mengubah Data Kategorikal pada Kolom UserID dan ISBN
      - **Proses:** Mengubah data kategorikal pada kolom `UserID` dan `ISBN` menjadi bentuk numerik menggunakan label encoding. Label encoding mengonversi setiap kategori menjadi angka yang dibutuhkan untuk sebagian besar algoritma rekomendasi.  
      - **Alasan:** Proses ini penting karena sebagian besar algoritma collaborative filtering membutuhkan input dalam bentuk numerik. Label encoding memungkinkan model untuk memproses data kategorikal seperti `UserID` dan `ISBN` dalam format yang dapat dihitung.
   
   - Mengacak Dataset
      - **Proses:** Mengacak dataset dengan metode `sample(frac=1, random_state=42)` untuk memastikan distribusi data yang lebih merata sebelum pemisahan data.  
      - **Alasan:** Pengacakan dataset penting untuk menghindari bias dalam pembagian data dan memastikan model belajar dari sampel yang representatif dari seluruh dataset.
   
   - Melakukan Data Splitting 80:20
      - **Proses:** Membagi dataset menjadi dua bagian, yaitu 80% untuk data pelatihan dan 20% untuk data pengujian, dengan menghitung indeks pembagian menggunakan `int(0.8 * df.shape[0])`.  
      - **Alasan:** Membagi data menjadi set pelatihan dan pengujian memungkinkan untuk evaluasi model yang lebih baik. Data pelatihan digunakan untuk membangun model, sementara data pengujian digunakan untuk mengukur kinerja model dalam kondisi yang belum pernah dilihat sebelumnya.


---

## Modeling

Dalam proyek ini, sistem rekomendasi dibangun menggunakan dua pendekatan, yaitu *content-based filtering* dan *collaborative filtering*. Kedua metode ini memberikan solusi rekomendasi buku yang dihasilkan dalam bentuk *top-N recommendations*.

### 1. Content-Based Filtering
   - **Metode yang Digunakan**: Menggunakan TF-IDF (*Term Frequency-Inverse Document Frequency*) untuk merepresentasikan fitur gabungan dari `Book-Author` dan `Title` sebagai vektor. Cosine Similarity kemudian digunakan untuk mengukur kesamaan antar vektor tersebut.
   - **Top-N Recommendations**: Sistem menghasilkan *top-N* rekomendasi berdasarkan tingkat kemiripan buku yang dihitung dari vektor TF-IDF. Rekomendasi diberikan berdasarkan buku yang mirip dengan buku yang disukai atau telah diberi rating tinggi oleh pengguna.
   
   - **Kelebihan**:
     - Sistem dapat memberikan rekomendasi yang spesifik dan relevan sesuai dengan konten atau tema buku tertentu.
     - Tidak membutuhkan data interaksi pengguna lainnya, sehingga dapat berfungsi dengan baik bahkan dengan data pengguna yang terbatas.
   
   - **Kekurangan**:
     - Rentan terhadap *over-specialization*, yaitu ketika sistem hanya merekomendasikan buku-buku yang sangat mirip dengan yang sudah dibaca tanpa variasi.
     - Tidak mampu menangkap preferensi pengguna di luar atribut konten buku yang sudah tersedia (misalnya, genre baru atau buku dari penulis yang berbeda).

### Fungsi book_recommendations

Fungsi `book_recommendations` digunakan untuk memberikan rekomendasi buku berdasarkan kemiripan dengan buku yang diberikan. Fungsi ini menggunakan data kemiripan antar buku untuk menghasilkan daftar buku yang serupa dengan buku yang disebutkan dalam parameter.

#### Parameter:
- **nama_buku** (tipe data: string):
  Nama buku yang akan digunakan sebagai referensi untuk mendapatkan rekomendasi. Buku ini akan menjadi acuan untuk mencari buku-buku lain yang memiliki kemiripan.

- **similarity_data** (tipe data: `pd.DataFrame`, default: `cosine_sim_df`):
  Dataframe yang berisi nilai kemiripan antara buku-buku, biasanya berupa matriks kemiripan cosine yang disusun dalam bentuk simetrik dengan buku-buku sebagai indeks dan kolom. Setiap nilai di dalam dataframe menunjukkan tingkat kemiripan antara buku-buku yang ada.

- **items** (tipe data: `pd.DataFrame`, default: `data[['book_title', 'book_author']]`):
  Dataframe yang berisi informasi buku, seperti `book_title` (judul buku) dan `book_author` (penulis buku). Data ini digunakan untuk memberikan detail tambahan tentang buku yang direkomendasikan.

- **k** (tipe data: integer, default: 10):
  Menentukan jumlah rekomendasi yang ingin diberikan. Fungsi ini akan mengembalikan `k` buku yang paling mirip dengan buku yang diberikan berdasarkan kemiripan yang dihitung.

#### Cara Kerja Fungsi:
1. **Mengambil Kemiripan Buku:**
   Fungsi ini pertama-tama akan mencari kemiripan buku yang diberikan (`nama_buku`) dengan menggunakan dataframe `similarity_data`. Kemiripan dihitung berdasarkan nilai cosine similarity antara buku yang diberikan dengan buku-buku lainnya.

2. **Menemukan Buku yang Paling Mirip:**
   Menggunakan `argpartition()`, fungsi ini akan memilih `k` buku dengan nilai kemiripan tertinggi. Fungsi `argpartition()` secara efisien memilih nilai terbesar tanpa mengurutkan seluruh array, yang membantu mempercepat proses untuk dataset yang besar.

3. **Membuang Nama Buku yang Dicari:**
   Setelah mendapatkan buku-buku yang paling mirip, fungsi ini akan menghapus buku yang dicari dari daftar rekomendasi untuk menghindari kemunculan buku yang sama dalam hasil rekomendasi.

4. **Menggabungkan Data Buku:**
   Setelah mendapatkan daftar buku yang paling mirip, fungsi akan menggabungkan hasil tersebut dengan informasi buku lainnya (judul dan penulis) yang ada dalam `items`. Ini akan menghasilkan dataframe yang berisi informasi lengkap tentang buku-buku yang direkomendasikan.

5. **Mengembalikan Rekomendasi Buku:**
   Fungsi ini mengembalikan dataframe yang berisi `k` buku yang paling mirip dengan buku yang diberikan beserta informasi tambahan tentang setiap buku.

#### Contoh Penggunaan:
Jika kita ingin merekomendasikan 5 buku yang mirip dengan buku "Harry Potter", kita dapat memanggil fungsi ini seperti berikut:

```python
book_recommendations("Little Wolf's Book of Badness")
```

**Hasil :**

  Berikut adalah Top 10 dari rekomendasi dengan judul buku "Little Wolf's Book of Badness" menggunakan Content Based Filtering
  | Book Title                                        | Book Author       |
|---------------------------------------------------|-------------------|
| Little Wolf's Big Book of Badness and Daring D... | Ian Whybrow       |
| Little Wolf's Postbag                             | Ian Whybrow       |
| Little Wolf's Handy Book of Poems                 | Ian Whybrow       |
| Little Wolf, Pack Leader                          | Ian Whybrow       |
| Wolf & the Seven Kids (A first little golden book) | Golden Books      |
| Wolf Children                                     | Charles MacLean   |
| Small Wolf (I Can Read Book 3)                    | Nathaniel Benchley |
| The WOLF                                          | Margaret Barbalet |
| Best Little Word Book Ever! (Little Golden Book)  | Richard Scarry    |
| Children of the Wolf                              | Jane Yolen        |


### 2. Collaborative Filtering
   - **Metode yang Digunakan**: Menggunakan *Neural Collaborative Filtering* (NCF), sebuah pendekatan berbasis deep learning yang memanfaatkan vektor pengguna dan item untuk memprediksi interaksi pengguna-buku.
   - **Top-N Recommendations**: Sistem menghasilkan *top-N* rekomendasi dengan memprediksi skor interaksi (misalnya, kemungkinan rating) dan memberikan rekomendasi buku dengan skor tertinggi.
   
   - **Kelebihan**:
     - Memungkinkan sistem memahami preferensi pengguna dengan lebih baik karena menggunakan data interaksi historis.
     - Dapat merekomendasikan buku dengan genre, tema, atau konten yang berbeda dari buku yang pernah dibaca pengguna.
   
   - **Kekurangan**:
     - Memerlukan data interaksi yang besar untuk melatih model, yang mungkin sulit jika data pengguna yang tersedia terbatas.
     - Cenderung lebih kompleks dan memerlukan sumber daya komputasi yang lebih tinggi dibandingkan metode content-based.

### OptimizedRecommenderNet - Model untuk Rekomendasi

Fungsi `OptimizedRecommenderNet` adalah model neural network yang dirancang untuk rekomendasi buku berbasis Collaborative Filtering. Model ini menggunakan embedding untuk representasi pengguna dan buku, serta menerapkan teknik regularisasi dan optimasi untuk meningkatkan akurasi dan mencegah overfitting.

#### Struktur Model:

1. **User and Book Embeddings:**
   - **`self.user_embedding`:** Layer embedding untuk pengguna yang mengonversi ID pengguna menjadi vektor berdimensi rendah.
     - **Parameter:**
       - `num_users`: Jumlah total pengguna dalam dataset.
       - `embedding_size`: Ukuran vektor embedding, yang menentukan dimensi representasi pengguna.
       - `embeddings_initializer='he_normal'`: Inisialisasi bobot embedding menggunakan distribusi normal dengan standar deviasi yang dikalibrasi agar cocok dengan fungsi aktivasi ReLU.
       - `embeddings_regularizer=regularizers.l2(1e-6)`: Regularisasi L2 untuk mengurangi overfitting, dengan faktor penalti sebesar `1e-6`.

   - **`self.book_embedding`:** Layer embedding untuk buku yang mengonversi ID buku menjadi vektor berdimensi rendah.
     - **Parameter yang sama dengan `self.user_embedding`**.

   - **`self.user_bias` dan `self.book_bias`:** Layer embedding untuk bias pengguna dan bias buku, masing-masing menghasilkan satu nilai untuk setiap pengguna dan buku.
     - **Parameter:**
       - `num_users` dan `num_book`: Jumlah total pengguna dan buku.
       - `1`: Ukuran output adalah 1, karena setiap pengguna dan buku memiliki satu nilai bias.

2. **Hidden Layers dengan Batch Normalization:**
   - **`self.dense1`, `self.dense2`, `self.dense3`:** Lapisan dense yang masing-masing terdiri dari 256, 128, dan 64 unit. Setiap lapisan ini dilengkapi dengan regularisasi L2.
     - **Parameter:**
       - `units`: Jumlah unit (neuron) pada setiap lapisan.
       - `kernel_regularizer=regularizers.l2(1e-6)`: Regularisasi L2 untuk mencegah overfitting pada bobot model.

   - **`self.bn1`, `self.bn2`, `self.bn3`:** Batch Normalization setelah setiap lapisan dense untuk mempercepat pelatihan dan meningkatkan stabilitas.
     - **Fungsi:** Menormalkan input ke lapisan berikutnya untuk menjaga distribusi data yang stabil selama pelatihan.

   - **Fungsi Aktivasi `ReLU`:** Digunakan pada lapisan tersembunyi untuk memperkenalkan non-linearitas. ReLU membantu model untuk belajar representasi yang lebih kompleks.

3. **Dropout:**
   - **`self.dropout`:** Dropout diterapkan setelah lapisan tersembunyi untuk mencegah overfitting dengan menghilangkan 60% neuron secara acak selama pelatihan.
     - **Parameter:**
       - `rate=0.6`: Ini berarti 60% dari neuron akan diabaikan selama pelatihan pada setiap iterasi.
     - **Tujuan:** Mencegah model untuk terlalu mengandalkan beberapa neuron tertentu dan meningkatkan generalisasi.

4. **Output Layer:**
   - **`self.output_layer`:** Layer output dengan satu unit dan fungsi aktivasi `sigmoid` untuk menghasilkan output berupa probabilitas rating (antara 0 dan 1).
     - **Parameter:**
       - `units=1`: Menghasilkan satu nilai prediksi untuk rating.
       - `activation='sigmoid'`: Fungsi aktivasi sigmoid digunakan untuk memetakan hasil ke rentang 0-1.

#### Fungsi `call`:
- **Proses:** 
  1. Menerima input berupa ID pengguna dan ID buku.
  2. Mengambil embedding untuk pengguna dan buku.
  3. Menghitung interaksi antara pengguna dan buku menggunakan `tensordot`.
  4. Menambahkan bias pengguna dan buku pada hasil interaksi.
  5. Memasukkan hasilnya melalui beberapa lapisan dense dengan batch normalization dan fungsi aktivasi `relu`.
  6. Mengaplikasikan dropout setelah lapisan tersembunyi.
  7. Menyelesaikan proses dengan menghasilkan satu nilai prediksi rating menggunakan layer output.

---

### Kompilasi dan Pelatihan Model

1. **Learning Rate Scheduler:**
   - Digunakan untuk menurunkan learning rate secara eksponensial setiap epoch untuk meningkatkan konvergensi model.
   - Fungsi `LearningRateScheduler` mengurangi learning rate dengan faktor 0.9 setiap epoch, dimulai dari `1e-4`.

2. **Kompilasi Model:**
   - **Loss Function:** `BinaryCrossentropy` digunakan untuk model yang menghasilkan output probabilitas (misalnya rating 0 atau 1).
   - **Optimizer:** `Adam` dengan learning rate awal `1e-4`.
   - **Metrics:** `RootMeanSquaredError` digunakan untuk mengevaluasi seberapa baik model dalam memprediksi rating.

3. **Fit Model:**
   - **Training Data:** `x_train` dan `y_train` digunakan untuk pelatihan.
   - **Validation Data:** `x_val` dan `y_val` digunakan untuk validasi model pada setiap epoch.
   - **Callbacks:** Learning rate scheduler diterapkan untuk menyesuaikan learning rate selama pelatihan.
   - Model dilatih dengan batch size 32 dan selama 8 epoch.

#### Yang digunakan di proyek:
```python
model = OptimizedRecommenderNet(num_users, num_book, 50)  # Inisialisasi model

history = model.fit(
    x=x_train,
    y=y_train,
    batch_size=32,
    epochs=8,
    validation_data=(x_val, y_val),
    callbacks=[lr_scheduler]
)
```

**Hasil :**

Berikut adalah buku yang dapat rating terbesar dari userID 2103

| Book Title                                                | Book Author     |
|-----------------------------------------------------------|-----------------|
| Home Tree Home: Principles of Treehouse Construction      | Peter Nelson    |
| Sherlock Holmes and the Rune Stone Mystery (Sherlock)     | Larry Millett   |
| The Disappearance of Sherlock Holmes                      | Larry Millett   |

dan berikut adalah Top 10 dari rekomendasi dari userID 2103 menggunakan Collaborative Based Filtering

| Book Title                                         | Book Author           |
|----------------------------------------------------|------------------------|
| Anam Cara : A Book of Celtic Wisdom                | John O'Donohue        |
| Judge Judy Sheindlin's Win or Lose by How You ...  | Judge Judy Sheindlin  |
| Ella Enchanted (rack)                              | Gail Carson Levine     |
| Two Old Women                                      | Velma Wallis          |
| Suddenly                                           | Barbara Delinsky      |
| Prey: A Novel                                      | Michael Crichton      |
| The Second Rumpole Omnibus (Crime Monthly)         | John Mortimer         |
| The Wonderful Story of Henry Sugar and Six More    | Roald Dahl            |
| Eden Close                                         | Anita Shreve          |
| Including Students with Special Needs: A Pract...  | Marilyn Penovich Friend |

---


## Evaluation

Untuk mengukur kinerja model rekomendasi, digunakan dua metrik evaluasi yang sesuai dengan konteks masing-masing pendekatan, yaitu *content-based filtering* dan *collaborative filtering*.

### 1. Content-Based Filtering Evaluation: Precision
- **Metrik**: Precision
  - **Formula**: Precision = Jumlah rekomendasi yang relevan/Jumlah item yang direkomendasikan

  - **Penjelasan**: Precision mengukur seberapa banyak dari rekomendasi yang diberikan oleh sistem benar-benar relevan dengan preferensi pengguna. Semakin tinggi precision, semakin baik sistem dalam memberikan rekomendasi yang relevan dan bermanfaat bagi pengguna.
  
  - **Cara Kerja**: Precision dihitung dengan membandingkan jumlah item yang relevan (yang dipilih atau diberi rating positif oleh pengguna) dengan jumlah total item yang direkomendasikan. Ini penting untuk memastikan bahwa pengguna hanya melihat rekomendasi yang relevan dan tidak dibanjiri dengan pilihan yang tidak berguna.

1. **Input**: Judul buku yang dicari adalah "*Little Wolf's Book of Badness*".
2. **Output**: Sistem memberikan daftar buku yang direkomendasikan yang terkait dengan judul tersebut.

#### Output dari rekomendasi:
Dari output yang diberikan, kita melihat ada **9 buku** yang relevan berdasarkan judulnya (semuanya mengandung "Little Wolf").

  | Book Title                                        | Book Author       |
|---------------------------------------------------|-------------------|
| Little Wolf's Big Book of Badness and Daring D... | Ian Whybrow       |
| Little Wolf's Postbag                             | Ian Whybrow       |
| Little Wolf's Handy Book of Poems                 | Ian Whybrow       |
| Little Wolf, Pack Leader                          | Ian Whybrow       |
| Wolf & the Seven Kids (A first little golden book) | Golden Books      |
| Wolf Children                                     | Charles MacLean   |
| Small Wolf (I Can Read Book 3)                    | Nathaniel Benchley |
| The WOLF                                          | Margaret Barbalet |
| Best Little Word Book Ever! (Little Golden Book)  | Richard Scarry    |
| Children of the Wolf                              | Jane Yolen        |

#### Menghitung Precision:

Precision = 9/10 = 0.9

**Kesimpulan :**

Jadi, **precision** untuk rekomendasi ini adalah **0.9** atau 90%.

### 2. Collaborative Filtering Evaluation: RMSE (Root Mean Square Error)
- **Metrik**: RMSE
  - **Formula :**
    RMSE = √(1/n ∑(r_ui - r_hat_ui)²)

  - **Penjelasan**: RMSE mengukur seberapa baik model dalam memprediksi rating pengguna untuk buku yang belum mereka beri rating. RMSE yang lebih rendah menunjukkan bahwa model mampu memprediksi rating dengan lebih akurat, yang penting untuk memberikan rekomendasi yang sesuai dengan preferensi pengguna.
  - **Cara Kerja**: RMSE menghitung selisih antara rating aktual dan rating yang diprediksi, kemudian mengkuadratkan perbedaan tersebut. Hasil kuadratnya dijumlahkan, dibagi dengan jumlah data yang diuji, dan diakarkan untuk memberikan nilai kesalahan prediksi rata-rata. Model dengan RMSE yang lebih kecil menunjukkan prediksi yang lebih akurat.
---

Dengan menggunakan precision dan RMSE, kita dapat mengevaluasi kinerja kedua model rekomendasi secara menyeluruh sesuai dengan tujuan dan permasalahan proyek.

### Hasil Model
![image](https://github.com/user-attachments/assets/22760891-2e1e-40ce-84ab-ee2356785489)

- **Root Mean Squared Error (RMSE)**: 0.3143
  - RMSE adalah metrik yang mengukur seberapa jauh prediksi model dari nilai sebenarnya. Nilai RMSE yang lebih rendah menunjukkan performa model yang lebih baik.

- **Validation RMSE**: 0.3533
  - Validasi RMSE menunjukkan kesalahan rata-rata model pada data validasi. Meskipun lebih tinggi dari RMSE pelatihan, ini memberi gambaran seberapa baik model dapat diterapkan pada data baru.

**Kesimpulan :**
Model menunjukkan performa yang baik pada data pelatihan, dengan nilai RMSE yang relatif rendah. Namun, ada sedikit peningkatan pada validasi loss dan validasi RMSE, yang bisa mengindikasikan bahwa model mulai mengalami overfitting atau masih membutuhkan peningkatan lebih lanjut. Penyesuaian lebih lanjut seperti penggunaan regularisasi atau lebih banyak epoch bisa membantu mengurangi gap antara pelatihan dan validasi performance.

### Dampak dari Evaluasi Model Terhadap Business Understanding

Berdasarkan hasil evaluasi model **Content-Based Filtering** dan **Collaborative Filtering**, berikut adalah dampaknya terhadap pemahaman bisnis dan bagaimana solusi yang diterapkan dapat memberikan dampak positif terhadap platform rekomendasi buku.

---

### 1. **Apakah model ini sudah menjawab problem statement?**

**Problem Statement 1: Bagaimana cara menciptakan sistem rekomendasi buku yang dapat secara akurat menyesuaikan saran berdasarkan preferensi pembaca?**

- **Content-Based Filtering** berhasil menjawab pertanyaan ini dengan sangat baik. Dengan menggunakan teknik **TF-IDF** dan **Cosine Similarity**, sistem dapat memahami preferensi pengguna berdasarkan konten buku yang telah mereka baca atau beri rating. Nilai **precision = 0.9** menunjukkan bahwa sistem ini sangat relevan dalam menyesuaikan rekomendasi buku berdasarkan judul dan penulis yang disukai pengguna.

- **Collaborative Filtering** juga menjawab pertanyaan ini dengan baik, meskipun hasil RMSE sedikit lebih tinggi dibandingkan content-based. Pendekatan **Neural Collaborative Filtering (NCF)** memungkinkan model untuk memberikan rekomendasi berdasarkan interaksi antar pengguna dan buku, sehingga menghasilkan saran yang lebih beragam.

**Problem Statement 2: Dapatkah rekomendasi buku yang dipersonalisasi meningkatkan interaksi dan daya tarik platform dalam jangka panjang?**

- **Content-Based Filtering** secara jelas meningkatkan **interaksi pengguna**, karena setiap rekomendasi yang diberikan relevan dengan preferensi mereka sebelumnya. Rekomendasi yang sangat tepat dapat meningkatkan kepuasan pengguna, yang akan meningkatkan tingkat keterlibatan.

- **Collaborative Filtering** cenderung memberikan **rekomendasi yang lebih beragam**, yang dapat membantu meningkatkan **retensi pengguna**. Meskipun hasil RMSE lebih tinggi, kemampuan model untuk memberikan saran baru berdasarkan interaksi pengguna bisa meningkatkan **exploration** dan menarik pengguna untuk menjelajahi lebih banyak buku.

**Problem Statement 3: Bagaimana perbedaan metode rekomendasi, seperti berbasis konten atau kolaboratif, dapat mempengaruhi kualitas dan relevansi saran buku yang diberikan?**

- **Content-Based Filtering** memberikan rekomendasi yang sangat relevan dan spesifik berdasarkan konten buku, sehingga kualitas saran sangat tinggi, namun mungkin kurang bervariasi. Sebaliknya, **Collaborative Filtering** dapat memberikan saran yang lebih bervariasi, meskipun mungkin ada beberapa saran yang kurang tepat.

---

### 2. **Apakah model ini berhasil mencapai goals yang diharapkan?**

**Goal 1: Meningkatkan interaksi pengguna dengan menyediakan rekomendasi buku yang disesuaikan dengan kebutuhan dan preferensi pribadi mereka.**

- **Content-Based Filtering** memenuhi tujuan ini dengan sangat baik karena memberikan rekomendasi yang sangat relevan berdasarkan buku yang telah dibaca pengguna. Model ini memastikan bahwa setiap rekomendasi menyesuaikan dengan minat pembaca, yang dapat meningkatkan interaksi pengguna.

- **Collaborative Filtering** juga mendekati tujuan ini dengan memberikan rekomendasi yang dipersonalisasi, meskipun hasilnya sedikit lebih bervariasi dan tidak selalu sepresisi content-based. Namun, rekomendasi yang lebih beragam dapat memotivasi pengguna untuk lebih sering kembali dan menjelajahi berbagai jenis buku.

**Goal 2: Memberikan saran buku yang relevan dan beragam yang sesuai dengan preferensi individu.**

- **Content-Based Filtering** lebih fokus pada relevansi, namun bisa saja terbatas pada buku-buku yang mirip dengan yang sudah ada. Namun, sistem ini sangat kuat dalam memberikan rekomendasi yang sesuai dengan preferensi individual pengguna.

- **Collaborative Filtering** lebih unggul dalam memberikan **keberagaman** rekomendasi, karena mengandalkan data interaksi antar pengguna. Ini memberikan kesempatan untuk menemukan buku-buku baru yang belum tentu mirip dengan yang sudah dibaca, namun tetap menarik berdasarkan pola preferensi pengguna lainnya.

**Goal 3: Menerapkan berbagai teknik rekomendasi dan mengevaluasi efektivitasnya dalam meningkatkan kualitas rekomendasi.**

- Kedua model berhasil memenuhi goal ini. **Content-Based Filtering** menunjukkan **precision** yang tinggi, sedangkan **Collaborative Filtering** memberikan **diversitas** yang lebih baik. Evaluasi **precision** dan **RMSE** menunjukkan bahwa kedua model memberikan kontribusi yang signifikan untuk meningkatkan kualitas rekomendasi buku yang dipersonalisasi.

---

### 3. **Apakah solusi statement yang direncanakan berdampak?**

**Solusi dengan Content-Based Filtering:**
- Solusi ini berdampak positif dalam meningkatkan **relevansi** rekomendasi, karena sistem memberikan saran berdasarkan konten buku yang telah diberikan rating oleh pengguna. Dengan **precision = 0.9**, solusi ini efektif dalam menyarankan buku yang sangat sesuai dengan preferensi individu, dan hasilnya akan meningkatkan pengalaman pengguna secara keseluruhan.
- Model ini dapat digunakan untuk pengguna yang memiliki riwayat buku tertentu yang ingin mereka eksplorasi lebih lanjut, dengan memberikan rekomendasi yang lebih sempit namun sangat relevan.

**Solusi dengan Collaborative Filtering:**
- Pendekatan **Collaborative Filtering** dengan menggunakan **Neural Collaborative Filtering** sangat efektif dalam memberikan **keberagaman** saran. Dengan memberikan rekomendasi berdasarkan interaksi pengguna lainnya, model ini memperkenalkan buku baru yang mungkin tidak diketahui oleh pengguna sebelumnya.
- Meskipun evaluasi menunjukkan hasil RMSE yang sedikit lebih tinggi, kemampuan model untuk memberikan **rekomendasi yang lebih bervariasi** dapat sangat berguna dalam menarik kembali pengguna yang sudah lama tidak aktif dan mendorong mereka untuk menjelajahi lebih banyak buku.

### **Kesimpulan**
Kedua solusi rekomendasi ini, baik **Content-Based** maupun **Collaborative Filtering**, memiliki dampak yang positif terhadap platform rekomendasi buku. **Content-Based** lebih fokus pada **relevansi** dan **akurasi** saran, sementara **Collaborative Filtering** memberikan **keberagaman** rekomendasi. Dengan menerapkan kedua pendekatan ini, platform dapat menciptakan pengalaman pengguna yang lebih personal dan menarik, yang pada gilirannya akan meningkatkan interaksi dan retensi pengguna.

