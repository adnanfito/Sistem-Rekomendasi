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

- Banyak pembaca kesulitan menemukan buku yang sesuai dengan minat atau preferensi mereka karena jumlah buku yang terus berkembang.
- Pilihan buku yang banyak membuat pengguna merasa kewalahan atau kehilangan minat dalam mencari buku yang relevan.
- Platform buku, seperti toko buku online atau perpustakaan digital, menghadapi tantangan dalam menyajikan rekomendasi yang akurat dan personal kepada pengguna.
- Pengalaman pengguna yang kurang memuaskan berpotensi menurunkan keterlibatan dan loyalitas pengguna.

## Goals (Tujuan)

- Membangun sistem rekomendasi buku yang memberikan rekomendasi relevan dan personal berdasarkan preferensi atau perilaku pengguna.
- Mempermudah pengguna dalam menemukan buku yang sesuai dengan minat mereka untuk meningkatkan pengalaman membaca.
- Meningkatkan minat baca di kalangan masyarakat dengan menyediakan rekomendasi buku yang tepat dan menarik.
- Membantu platform buku meningkatkan keterlibatan pengguna dan mengoptimalkan pengalaman berbelanja atau meminjam buku.

## Solution Approach

Untuk meraih tujuan di atas, terdapat dua pendekatan yang dapat digunakan dalam membangun sistem rekomendasi buku:

### 1. Content-Based Filtering

Pendekatan ini menggunakan informasi tentang buku itu sendiri (seperti genre, penulis, atau kata kunci) untuk memberikan rekomendasi kepada pengguna. Setiap buku akan diproses untuk menentukan karakteristik utamanya, kemudian sistem akan mencocokkan buku yang memiliki kemiripan dengan buku yang sudah dibaca atau disukai oleh pengguna sebelumnya. Keunggulan dari pendekatan ini adalah bahwa sistem ini dapat memberikan rekomendasi yang sangat relevan berdasarkan kesukaan spesifik pengguna, meskipun pendekatan ini kurang dapat menyarankan buku yang tidak dikenal oleh pengguna.

#### Langkah-langkah implementasi:
- Ekstraksi fitur dari buku (genre, pengarang, kata kunci, dsb).
- Membangun profil pengguna berdasarkan buku yang pernah dibaca atau disukai.
- Menyajikan rekomendasi buku berdasarkan kesamaan fitur antara buku yang telah dibaca dan buku lainnya.

### 2. Collaborative Filtering

Pendekatan ini berfokus pada perilaku atau preferensi pengguna lain yang serupa untuk memberikan rekomendasi. Dalam Collaborative Filtering, sistem tidak memerlukan informasi eksplisit tentang konten buku. Sebagai gantinya, sistem menganalisis pola perilaku pengguna, seperti buku yang sering dibaca atau dinilai tinggi oleh kelompok pengguna yang mirip. Pendekatan ini dapat memberikan rekomendasi yang lebih beragam dan menarik, bahkan untuk buku yang belum pernah dibaca oleh pengguna sebelumnya.

#### Langkah-langkah implementasi:
- Pengumpulan data interaksi pengguna dengan buku (rating buku).
- Mencari pengguna yang memiliki preferensi serupa dengan pengguna target.
- Memberikan rekomendasi berdasarkan preferensi pengguna serupa.

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
   - **Missing Value Handling**: Menangani nilai yang hilang pada kolom `Book-Title`, `Book-Author`, `Year-Of-Publication`, dan `Publisher` dengan menghapus atau mengisi nilai kosong. Tahap ini bertujuan agar data yang digunakan pada model lengkap dan reliabel.
     - **Alasan**: Kolom-kolom ini berisi informasi penting untuk rekomendasi. Mengatasi nilai yang hilang membantu meningkatkan akurasi dan validitas model dengan data yang tidak memiliki kekosongan signifikan.

   - **Drop Duplicates**: Menghapus duplikasi baris dalam data untuk menghindari pengaruh ganda dari data yang sama dalam hasil rekomendasi. Data yang duplikat bisa mengubah distribusi dan menyebabkan model belajar dari data yang berlebihan.
     - **Alasan**: Menghindari data duplikat penting agar model tidak overfitting pada informasi yang sama secara berlebihan, yang dapat mengurangi kualitas rekomendasi.

2. **Content-Based Filtering**:
   - **TF-IDF (Term Frequency-Inverse Document Frequency)**: Menggunakan TF-IDF untuk menghitung representasi bobot fitur gabungan dari `Book-Author` dan `Title`. Teknik ini mengekstrak informasi penting dari teks untuk memberi bobot pada istilah yang muncul unik pada buku tertentu.
     - **Alasan**: Dengan menggabungkan `Book-Author` dan `Title`, model memahami karakteristik konten buku secara lebih spesifik. TF-IDF membantu mengidentifikasi buku yang mirip berdasarkan kombinasi penulis dan judul, sehingga meningkatkan relevansi rekomendasi konten.

3. **Collaborative Filtering**:
   - **Encoding & Label Encoding**: Mengubah data kategorikal pada kolom `UserID` dan `ISBN` menjadi bentuk numerik agar dapat diproses oleh model collaborative filtering. Label encoding mengonversi setiap kategori menjadi angka yang dibutuhkan untuk sebagian besar algoritma rekomendasi.
     - **Alasan**: Encoding memungkinkan model untuk memahami data kategorikal seperti `UserID` dan `ISBN` dalam format numerik, yang esensial untuk mendeteksi pola preferensi pengguna.

   - **Data Splitting**: Memisahkan data menjadi bagian training dan testing untuk evaluasi model. Pemisahan data penting agar performa model dapat diuji pada data yang belum pernah dilihat model sebelumnya, sehingga hasilnya lebih akurat dan bisa digunakan untuk memprediksi rating atau interaksi buku yang belum ada.
     - **Alasan**: Data splitting memastikan bahwa model dilatih dan diuji dengan data yang berbeda, sehingga hasilnya dapat dievaluasi secara objektif dan performanya pada data baru dapat diperkirakan dengan lebih baik.

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

**Hasil**

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
    
**Hasil**

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
  - **Formula**:
    
  $$
  \text{Precision} = \frac{\text{Jumlah rekomendasi yang relevan}}{\text{Jumlah item yang direkomendasikan}}
  $$

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
$$
\text{Precision} = \frac{9}{10} = 0.9
$$

**Kesimpulan :**

Jadi, **precision** untuk rekomendasi ini adalah **0.9** atau 90%.

### 2. Collaborative Filtering Evaluation: RMSE (Root Mean Square Error)
- **Metrik**: RMSE
  - **Formula**:
    
$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (r_{ui} - \hat{r}_{ui})^2}
$$
    
Di mana:

$$ \( r_{ui} \) $$ 

adalah rating aktual yang diberikan oleh pengguna \( u \) untuk item \( i \),

$$ \( \hat{r}_{ui} \) $$ 

adalah rating yang diprediksi oleh model untuk item \( i \),

$$ \( n \) $$ 

adalah jumlah data yang diuji.
  
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

## Conclusion

Proyek sistem rekomendasi buku ini berhasil menghasilkan dua pendekatan utama dalam memberikan rekomendasi yang relevan bagi pengguna: **Content-Based Filtering** dan **Collaborative Filtering**. Berdasarkan evaluasi performa masing-masing model, berikut adalah hasil yang diperoleh:

### 1. Content-Based Filtering
- **Evaluasi**: Precision = 0.9
- **Kesimpulan**: Pendekatan content-based menggunakan teknik TF-IDF dan Cosine Similarity menunjukkan hasil yang sangat baik dengan nilai precision 0.9. Ini menunjukkan bahwa rekomendasi yang dihasilkan sangat relevan dengan preferensi pengguna berdasarkan fitur konten buku seperti judul dan penulis. Sistem ini efektif dalam memberikan rekomendasi buku yang mirip dengan buku yang telah diberi rating oleh pengguna.

### 2. Collaborative Filtering
- **Evaluasi**: RMSE = 0.3143, val_RMSE = 0.3533
- **Kesimpulan**: Pendekatan collaborative filtering menggunakan Neural Collaborative Filtering (NCF) memberikan performa yang cukup baik dengan nilai RMSE sebesar 0.3143 pada data latih dan 0.3533 pada data validasi. Nilai RMSE yang lebih rendah menunjukkan bahwa model ini mampu memprediksi rating dengan akurat dan memberikan rekomendasi yang sesuai dengan preferensi pengguna berdasarkan interaksi mereka dengan buku-buku lainnya.

### Perbandingan Kedua Pendekatan
- **Content-Based** lebih unggul dalam hal presisi, memberikan rekomendasi yang lebih relevan berdasarkan konten buku yang telah dibaca atau disukai pengguna.
- **Collaborative Filtering** memiliki kemampuan untuk memberikan rekomendasi yang lebih beragam dan memperhitungkan interaksi pengguna dengan banyak buku, meskipun hasil evaluasinya sedikit lebih rendah dibandingkan content-based.

Secara keseluruhan, kedua pendekatan tersebut saling melengkapi dan dapat digunakan bersamaan untuk meningkatkan kualitas rekomendasi buku yang lebih akurat dan beragam untuk pengguna.
