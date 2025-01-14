# Machine Learning Terapan Submission Kedua | Sistem Rekomendasi Tempat Wisata di Indonesia

### Disusun oleh : Setya Wijayanta

## Daftar Isi

- [Project Domain](#project-domain)
- [Business Understanding](#business-understanding)
- [Data Understanding](#data-understanding)
- [Data Preparation](#data-preparation)
- [Modeling](#modeling)
- [Evaluation](#evaluation)
- [Kesimpulan](#kesimpulan)
- [Referensi](#referensi)

## 1. Project Domain
Ini adalah proyek kedua Rekomendation untuk memenuhi submission pertama Dicoding Kelas Machine Learning Terapan. Proyek ini membahas tentang sistem rekomendasi tempat wisata di Indonesia berdasarkan kategori, preferensi pengguna, dan penilaian pengguna lainnya.

### Latar Belakang
Indonesia dikenal salah satunya karena potensi luar biasa yang dimiliki dalam sektor pariwisata, dengan destinasi-destinasi yang tersebar di seluruh penjuru negeri. Potensi pariwisata ini menjadi salah satu daya tarik utama yang mampu menarik perhatian wisatawan, baik dari dalam negeri maupun mancanegara, untuk menjelajahi keindahan Indonesia (UNWTO, 2020). Keindahan alam Indonesia meliputi beragam lanskap menakjubkan, mulai dari pantai-pantai tropis yang memukau, pegunungan megah yang menjulang, hingga gugusan pulau-pulau kecil yang menawarkan pesona tak tertandingi (Badan Pusat Statistik, 2021). Selain itu, budaya dan tradisi yang khas, berakar pada sejarah dan keunikan masyarakat lokal, memberikan pengalaman autentik yang tidak hanya menghibur tetapi juga memperkaya wawasan wisatawan. Pariwisata di Indonesia juga memberikan kontribusi yang signifikan terhadap berbagai aspek, baik secara ekonomi sebagai sumber devisa negara, secara sosial melalui penciptaan peluang kerja, maupun secara budaya dengan memperkenalkan seni dan warisan tradisional Indonesia ke panggung global [1] (Kementerian Pariwisata dan Ekonomi Kreatif, 2022).

Namun, banyaknya pilihan destinasi wisata yang tersedia sering kali menjadi tantangan bagi wisatawan untuk menentukan lokasi yang paling sesuai dengan preferensi mereka. Sebagai solusi atas permasalahan ini, dikembangkanlah sistem rekomendasi destinasi wisata yang dirancang untuk mempermudah wisatawan dalam mengambil keputusan secara lebih terarah. Sistem ini bekerja dengan memanfaatkan data dari berbagai destinasi wisata yang ada, serta data perilaku pengguna, seperti penilaian dan ulasan dari kunjungan sebelumnya, yang kemudian diolah menggunakan pendekatan berbasis teknologi seperti collaborative filtering. Pendekatan ini memungkinkan sistem untuk menganalisis pola preferensi individu secara mendalam, sehingga dapat memberikan rekomendasi yang relevan dan personal. Dengan demikian, sistem ini terbukti efektif dalam menciptakan pengalaman wisata yang lebih terpersonalisasi, memungkinkan wisatawan untuk menemukan destinasi yang tidak hanya sesuai dengan kebutuhan mereka, tetapi juga memberikan nilai lebih dalam perjalanan mereka [2] (Muchamad Sulton Irwinsyah, 2019; Universitas Islam Sultan Agung, 2017).​

## 2. Business Understanding
Pengguna dari platform perjalanan atau destinasi wisata sering kali kesulitan menemukan tempat wisata yang sesuai dengan preferensi mereka, terutama jika terdapat banyak pilihan destinasi. Hal ini dapat menyebabkan pengalaman yang kurang memuaskan dan menurunkan retensi pengguna terhadap platform tersebut. Salah satu cara untuk meningkatkan pengalaman pengguna adalah dengan menggunakan sistem rekomendasi yang dapat membantu pengguna menemukan destinasi wisata yang relevan berdasarkan preferensi atau riwayat interaksi mereka.

### a. Problem Statements

Pada proyek ini, masalah yang akan dipecahkan adalah menyediakan rekomendasi yang relevan dan personal bagi pengguna, sehingga dapat mendorong keputusan pengguna untuk memilih destinasi tertentu, adapun melalui tahapan sebagai berikut :

1. Bagaimana memahami dan mengetahui terkait data dari dataset digunakan untuk pembuatan model sistem rekomendasi?
2. Bagaimana membuat model sistem rekomendasi dengan pendekatan content-based filtering?
3. Bagaimana membuat model sistem rekomendasi dengan pendekatan collaborative filtering?
4. Bagaimana cara mengevaluasi model sistem rekomendasi yang sudah dibuat?

### b. Goals

Berdasarkan masalah yang diidentifikasi di atas, maka tujuan dari proyek ini adalah menyediakan rekomendasi yang relevan dan personal bagi pengguna, sehingga dapat mendorong keputusan pengguna untuk memilih destinasi tertentu, adapun melalui tahapan sebagai berikut :

1. Melakukan langkah-langkah untuk memahami dataset terlebih dahulu, seperti EDA dan Visualisasi Data.
2. Membuat sistem rekomendasi film dengan content-based filtering.
3. Membuat sistem rekomendasi film dengan collaborative filtering.
4. Melakukan evaluasi terhadap model sistem rekomendasi yang telat dibuat.

### c. Solution Statements

Dari rumusan masalah dan tujuan di atas, maka disimpulkan beberapa solusi yang dapat dilakukan untuk mencapai tujuan dari proyek ini, yaitu membuat model yang dapat menyediakan rekomendasi yang relevan dan personal bagi pengguna, sehingga dapat mendorong keputusan pengguna untuk memilih destinasi tertentu, adapun melalui tahapan sebagai berikut :

1) Tahap persiapan data atau _data preparation_ dilakukan dengan menggunakan beberapa teknik persiapan data, yaitu:

   - Melakukan proses pengecekan data yang hilang atau _missing value_ pada data _places_ dan _ratings_.
   - Melakukan proses pengecekan data duplikat pada data _place_ dan _ratings_.

2) Tahap membuat model _machine learning_ yang dapat memberikan rekomendasi tempat wisata kepada pengguna berdasarkan _ratings_ atau penilaian pengguna terhadap tempat wisata tertentu. Tahap pembuatan model _machine learning_ untuk sistem rekomendasi menggunakan pendekatan _content-based filtering recommendation_ dan _collaborative filtering recommendation_.

   - **Content-based Filtering Recommendation**
   Dengan model ini hasil bisnis yang diharapkan dapat memperluas pengalaman pengguna dengan pilihan yang lebih relevan. 

     _Content-based filtering_ adalah pendekatan dalam sistem rekomendasi yang mendasarkan rekomendasi pada informasi karakteristik atau fitur dari item, seperti deskripsi, judul, atau kategori. Metode ini cocok digunakan ketika terdapat data yang cukup mengenai item yang direkomendasikan, seperti dalam sistem rekomendasi buku atau film. Penggunaannya melibatkan pencocokan fitur item dengan preferensi pengguna yang diidentifikasi dari data historis atau masukan langsung pengguna.

     - TF-IDF Vectorizer

       TF-IDF Vectorizer adalah salah satu alat yang sering digunakan dalam pendekatan content-based filtering. Alat ini mengubah teks menjadi representasi numerik (vektor fitur) dengan menghitung bobot setiap kata menggunakan metrik term frequency-inverse document frequency (TF-IDF). TF-IDF membantu menilai pentingnya suatu kata dalam sebuah dokumen relatif terhadap kumpulan dokumen lainnya. Hasilnya sering digunakan dalam model pembelajaran mesin untuk mengelompokkan atau mengklasifikasikan data teks. Penerapan metode ini terbukti mendukung efektivitas sistem rekomendasi dalam berbagai domain, termasuk hiburan dan e-commerce.

       TF-IDF menggunakan rumus untuk menghitung bobot masing-masing dokumen terhadap kata kunci, yaitu, [3]( Jurnal Sistem Informasi (2024). Penerapan Content-Based Filtering untuk sistem rekomendasi komik menggunakan TF-IDF dan cosine similarity.)

     - Cosine Similarity

     Model _Content-based filtering_ ini akan menerapkan Cosine Similarity, yaitu sebuah metrik similarity yang mengukur kemiripan antara dua vektor. Metrik ini mengukur sudut yang terdapat antara kedua vektor tersebut.

   - **Collaborative Filtering Recommendation**
     Dengan model ini hasil bisnis yang diharapkan dapat memberikan rekomendasi tempat wisata yang cocok menggunakan interaksi pengguna yang terdahulu dengan item-item yang diberikan untuk memberikan rekomendasi kepada pengguna tentang item-item yang mungkin disukai oleh pengguna.

     Collaborative Filtering Recommendation adalah metode rekomendasi yang menggunakan informasi dari banyak orang untuk memberikan rekomendasi kepada seorang pengguna.  Collaborative Filtering Recommendation biasanya dilakukan dengan menggunakan algoritma yang mengklasifikasikan pengguna berdasarkan preferensi dan kemiripan dengan pengguna lain, kemudian menggunakan informasi tersebut untuk memberikan rekomendasi yang cocok untuk pengguna tersebut.

     Model _Collaborative Filtering Recommendation_ ini akan menerapkan RecommenderNet, yaitu model sistem rekomendasi berbasis Collaborative Filtering yang dirancang menggunakan arsitektur berbasis layer embedding. Model RecommenderNet menggunakan Embedding Layer untuk menghasilkan representasi tersembunyi pengguna dan tempat wisata. Representasi ini membantu model memahami pola hubungan antara pengguna dan tempat yang mungkin tidak langsung terlihat. Kombinasi embedding, bias, dan operasi dot product memungkinkan model memprediksi kecocokan (rating) dengan akurat.

## 3. Data Understanding

a. Menampilkan informasi masing-masing dataset yaitu tourism_with_id.csv dan tourism_rating.csv menggunakan library pandas dari format .csv menjadi dataframe.
Dataset yang digunakan dalam proyek ini adalah dataset [4]Indonesia Tourism Destination yang diambil dari Kaggle dengan `tourism_with_id.csv` dan `tourism_rating.csv` sebagai dataset yang digunakan.

Dataset tersebut dapat diunduh [disini](https://www.kaggle.com/datasets/aprabowo/indonesia-tourism-destination)

- **Pengecekan informasi variabel**

  **Tabel 1. Informasi Dataset tourism_with_id**

  | #   | Column       | Non-Null Count | Dtype   |
  | --- | ------------ | -------------- | ------- |
  | 0   | Place_Id     | 437 non-null   | int64   |
  | 1   | Place_Name   | 437 non-null   | object  |
  | 2   | Description  | 437 non-null   | object  |
  | 3   | Category     | 437 non-null   | object  |
  | 4   | City         | 437 non-null   | object  |
  | 5   | Price        | 437 non-null   | int64   |
  | 6   | Rating       | 437 non-null   | float64 |
  | 7   | Time_Minutes | 205 non-null   | float64 |
  | 8   | Coordinate   | 437 non-null   | object  |
  | 9   | Lat          | 437 non-null   | float64 |
  | 10  | Long         | 437 non-null   | float64 |

  tourism_with_id terdiri dari 437 baris dan 10 kolom sebagai berikut:

  - Place_Id: kolom yang menunjukkan id dari setiap tempat wisata.
  - Place_Name: kolom yang menunjukkan nama dari setiap tempat wisata.
  - Description: kolom yang menunjukkan deskripsi dari setiap tempat wisata.
  - Category: kolom yang menunjukkan kategori dari setiap tempat wisata.
  - City: kolom yang menunjukkan kota dimana tempat wisata tersebut berada.
  - Price: kolom yang menunjukkan harga tiket masuk ke tempat wisata tersebut.
  - Rating: kolom yang menunjukkan rating dari setiap tempat wisata.
  - Time_Minutes: kolom yang menunjukkan waktu yang diperlukan untuk mengunjungi tempat wisata tersebut.
  - Coordinate: kolom yang menunjukkan koordinat dari setiap tempat wisata.
  - Lat: kolom yang menunjukkan latitude dari setiap tempat wisata.
  - Long: kolom yang menunjukkan longitude dari setiap tempat wisata.

b. Melakukan proses eksplorasi data investigasi awal pada data untuk menganalisis karakteristik, menemukan pola, anomali, dan memeriksa asumsi pada data.

Berikut adalah _Exploratory Data Analysis_ (EDA) yang merupakan proses investigasi awal pada data untuk menganalisis karakteristik, menemukan pola, anomali, dan memeriksa asumsi pada data. Dengan melakukan pengecekan deskripsi statistik dataset places dengan fitur describe(). 

**Tabel 2. Deskripsi statistik dataset ratings**

|     # |      User_Id |     Place_Id | Place_Ratings |
|------:|-------------:|-------------:|--------------:|
| count | 10000.000000 | 10000.000000 |  10000.000000 |
|  mean |   151.292700 |   219.416400 |      3.066500 |
|  std  |    86.137374 |   126.228335 |      1.379952 |
|  min  |     1.000000 |     1.000000 |      1.000000 |
|  25%  |    77.000000 |   108.750000 |      2.000000 |
|  50%  |   151.000000 |   220.000000 |      3.000000 |
|  75%  |   226.000000 |   329.000000 |      4.000000 |
|  max  |   300.000000 |   437.000000 |      5.000000 |

Berdasarkan output diatas, didapatkan deskripsi statistik yaitu:

count: Jumlah sampel data
mean: Nilai rata-rata
std: Standar deviasi
min: Nilai minimum
25%: Kuartil bawah/Q1
50%: Kuartil tengah/Q2/median
75%: Kuartil atas/Q3
max: Nilai maksimum

c. Pengecekan informasi variabel dari dataset ratings berupa jumlah kolom, nama kolom, jumlah data per kolom dan tipe datanya.

File ini terdiri dari 3 kolom sebagai berikut:

User_Id: identitas unik dari setiap pengguna.
Place_Id: identitas unik dari setiap tempat wisata.
Place_Ratings: penilaian atau rating yang diberikan oleh pengguna terhadap tempat wisata tertentu.

  Berikut adalah visualisasi dari dataset tourism_with_id:

  **Tabel 3. Sampel Dataset tourism_with_id**

  | #   | Place_Id | Place_Name                        | Category      |
  | --- | -------- | --------------------------------- | ------------- |
  | 0   | 1        | Monumen Nasional                  | Budaya        |
  | 1   | 2        | Kota Tua                          | Budaya        |
  | 2   | 3        | Dunia Fantasi                     | Taman Hiburan |
  | 3   | 4        | Taman Mini Indonesia Indah (TMII) | Taman Hiburan |
  | 4   | 5        | Atlantis Water Adventure          | Taman Hiburan |

 **Gambar 1. Distribusi Rating Rata-Rata Tempat Wisata**

![gambar_1](https://github.com/user-attachments/assets/4bdfba23-3e8a-496d-88f8-8d2dacbca9ee)

- **Rating**

  **Tabel 4. Informasi Dataset tourism_rating**

  | #   | Column        | Non-Null Count | Dtype |
  | --- | ------------- | -------------- | ----- |
  | 0   | User_Id       | 10000 non-null | int64 |
  | 1   | Place_Id      | 10000 non-null | int64 |
  | 2   | Place_Ratings | 10000 non-null | int64 |

  tourism_rating terdiri dari 10000 baris dan 3 kolom sebagai berikut:

  - User_Id: identitas unik dari setiap pengguna.
  - Place_Id: identitas unik dari setiap tempat wisata.
  - Place_Ratings: penilaian atau rating yang diberikan oleh pengguna terhadap tempat wisata tertentu.

- **Visualisasi Dataset Ratings**

  Visualisasi data adalah proses representasi grafis dari informasi dan data. Dengan menggunakan elemen visual seperti grafik, diagram, dan peta, visualisasi data menyediakan cara yang intuitif dan mudah diakses untuk melihat dan memahami tren, anomali, dan pola dalam data. Tujuan utama dari visualisasi data adalah untuk mengkomunikasikan informasi secara jelas dan efisien kepada pengguna, sehingga memudahkan pemahaman, analisis, dan pengambilan keputusan berdasarkan data tersebut

  Berikut adalah visualisasi dari dataset tourism_rating:

  **Tabel 5. Sampel Dataset tourism_rating**

  | #   | User_Id | Place_Id | Place_Ratings |
  | --- | ------- | -------- | ------------- |
  | 0   | 1       | 179      | 3             |
  | 1   | 1       | 344      | 2             |
  | 2   | 1       | 5        | 5             |
  | 3   | 1       | 373      | 3             |
  | 4   | 1       | 101      | 4             |

## 4. Data Preparation

Tahap ini bertujuan untuk mempersiapkan data yang akan digunakan untuk proses training model. Di sini dilakukan penghapusan kolom yang tidak diperlukan, pembersihkan data _missing value_, dan melakukan pengecekan dan penghapusan data duplikat.

a. **Data Preparation Content-Based Filtering**
  Tahap data preparation merupakan proses transformasi data menjadi bentuk yang dapat diterima oleh model machine learning nanti. Proses data preparation yang dilakukan, yaitu membersihkan data missing value, dan melakukan penghapusan data duplikat.

1) Menghapus Kolom yang Tidak Diperlukan
  Hanya kolom Place_Id, Place_Name, dan Category yang dipertahankan. Kolom lain yang tidak relevan dihapus.

2) Handle Missing Values
_Missing Value_ terjadi ketika variabel atau barus tertentu kekurangan titik data, sehingga menghasilkan informasi yang tidak lengkap. Nilai yang hilang dapat ditangani dengan berbagai cara seperti imputasi (mengisi nilai yang hilang dengan mean, median, modus, dll), atau penghapusan (menghilangkan baris atau kolom yang nilai hilang)

  Tidak ditemukan data hilang dalam dataset tourism_with_id.

3) Menghapus Data Duplikat
  Data duplikat adalah baris data yang sama persis untuk setiap variabel yang ada. Dataset yang digunakan perlu diperiksa juga apakah dataset memiliki data yang sama atau data duplikat. Jika ada, maka data tersebut harus ditangani dengan menghapus data duplikat tersebut.
  Data duplikat dihapus berdasarkan kombinasi kolom Place_Id dan Place_Name untuk memastikan keunikan data.
  Jumlah data places yang duplikat: 0
  Jumlah data rating yang duplikat: 79

  Berdasarkan hasil tersebut, ditemukan adanya data duplikat pada data rating, sehingga perlu dilakukan penghapusan data duplikat.

4) Dataset Ratings
  Pengecekan informasi variabel dari dataset ratings berupa jumlah kolom, nama kolom, jumlah data per kolom dan tipe datanya.

5) Menggunakan TF-IDF Vectorizer
   TF-IDF (Term Frequency-Inverse Document Frequency) adalah metode pemrosesan data yang dilakukan untuk mengukur pentingnya sebuah kata dalam sebuah dokumen relatif terhadap kumpulan dokumen lainnya. TF-IDF Vectorizer digunakan untuk menemukan representasi fitur yang penting dari setiap kategori destinasi wisata. Alat ini dari library scikit-learn akan mengubah nilai-nilai tersebut menjadi vektor dengan menggunakan metode fit_transform dan transform, serta melakukan pemecahan data menjadi bagian-bagian yang lebih kecil secara langsung.


b. **Data Preparation Collaborative Filtering**

1) Encoding Fitur

  Fitur User_Id dan Place_Id pada dataset tourism_rating diencoding menjadi array agar dapat diproses oleh model machine learning.

2) Melakukan mapping atau pemetaan kolom user dan place ke dataset ratings yang berkaitan.

3) Melakukan pengecekan jumlah user, jumlah tempat, penilaian minimal, dan penilaian maksimal.

4) Mengacak dataset ratings, pengacakan data dilakukan untuk menghindari adanya bias dalam proses pembelajaran model.

5) Normalisasi dataset ratings, normalisasi rating dilakukan untuk memastikan semua nilai berada dalam rentang tertentu.
    
6) Membagi dataset menjadi data train dan data test, yaitu sebesar 20% data uji dan 80% data latih.


## 5. Modeling and Result

Pada tahap pengembangan model _machine learning_ sistem rekomendasi, teknik _content-based filtering recommendation_ dan _collaborative filtering recommendation_ digunakan untuk memberikan rekomendasi tempat terbaik kepada pengguna berdasarkan rating atau penilaian yang telah mereka berikan pada tempat tersebut. Tujuannya adalah untuk memberikan hasil rekomendasi yang tepat sesuai dengan keinginan pengguna.

a. **Content-based Filtering Recommendation**

Beberapa tahap yang dilakukan untuk membuat sistem rekomendasi dengan pendekatan _content-based filtering_ adalah _cosine similarity_, dan pengujian sistem rekomendasi.

### Tahapan Model Content-based Filtering Recommendation

- Cosine Similarity

  Cosine similarity digunakan untuk menghitung tingkat kesamaan antara dua data place dengan mengukur sudut antara kedua data tersebut. Teknik ini menghitung tingkat kesamaan dengan menggunakan sudut antara data place yang dianalisis. Hasil perhitungan ini akan memberikan nilai yang menunjukkan tingkat kesamaan antara dua data place, dimana nilai yang mendekati 1 menunjukkan tingkat kesamaan yang tinggi, dan nilai yang mendekati 0 menunjukkan tingkat kesamaan yang rendah. Tahapan dalam cosine similarity adalah sebagai berikut :

  - Melakukan perhitungan derajat kesamaan atau similatiry degree antar nama tempat wisata dengan teknik cosine similarity menggunakan library scikit-learn.
  
  - Mengubah matriks cosine similarity menjadi bentuk dataframe antar nama tempat (destinasi wisata).

  - Melakukan pendefinisian fungsi place_recommendations untuk menampilkan hasil rekomendasi tempat berdasarkan kesamaan kategori dari sebuah tempat.

  - Hasil _Top-N Recommendation_

  Setelah data tempat wisata dikonversi menjadi matriks dengan menggunakan TF-IDF Vectorizer, dan tingkat kesamaan antar nama tempat ditentukan dengan menggunakan cosine similarity, selanjutnya dilakukan pengujian terhadap sistem rekomendasi yang menggunakan pendekatan content-based filtering recommendation. Hasil pengujian tersebut dapat dilihat sebagai berikut:

  Diambil sebuah nama tempat yang dipilih oleh pengguna.

  **Tabel 6. Nama Tempat yang Dipilih Pengguna**

|   # | Place_Id | Place_Name          | Category |
|----:|---------:|---------------------|----------|
| 176 | 177      | Pantai Parangtritis | Bahari   |

  Berikut adalah hasil rekomendasi nama tempat berdasarkan kategori yang sama.

  **Tabel 7. Hasil Rekomendasi _Content-based Filtering_**

| # |         Place_Name | Category |
|--:|-------------------:|---------:|
| 0 | Pantai Pok Tunggal |   Bahari |
| 1 |       Pantai Drini |   Bahari |
| 2 |    Pantai Sadranan |   Bahari |
| 3 |       Pantai Samas |   Bahari |
| 4 |    Pantai Nguluran |   Bahari |

  Berdasarkan hasil rekomendasi di atas, dapat dilihat bahwa sistem yang dibuat berhasil memberikan rekomendasi tempat berdasarkan sebuah tempat, yaitu 'Pantai Parangtritis' dan dihasilkan rekomendasi tempat dengan kategori yang sama, yaitu bahari.

b. **Model dengan Collaborative Filtering**

Collaborative Filtering adalah teknik merekomendasikan item yang mirip dengan preferensi pengguna yang sama di masa lalu, misalnya berdasarkan penilaian tempat yang telah diberikan oleh seorang pengguna. Sistem akan merekomendasikan tempat berdasarkan riwayat penilaian pengguna tersebut terhadap tempat dan kategorinya.

### Tahapan Model Collaborative Filtering 
Tahap-tahap yang dilakukan untuk membuat sistem rekomendasi dengan pendekatan _collaborative filtering_ meliputi : Melakukan pendefinisian kelas RecommenderNet untuk membangun model klasifikasi teks tersebut. 
RecommenderNet adalah model sistem rekomendasi berbasis Collaborative Filtering yang dirancang menggunakan arsitektur berbasis layer embedding. Model RecommenderNet menggunakan Embedding Layer untuk menghasilkan representasi tersembunyi pengguna dan tempat wisata. Representasi ini membantu model memahami pola hubungan antara pengguna dan tempat yang mungkin tidak langsung terlihat. Kombinasi embedding, bias, dan operasi dot product memungkinkan model memprediksi kecocokan (rating) dengan akurat.
Model ini akan memberikan rekomendasi kepada pengguna berdasarkan preferensi atau kecenderungan pengguna di masa lalu. RecommenderNet menggunakan algoritma pembelajaran mesin seperti collaborative filtering atau content-based filtering untuk menentukan rekomendasi yang tepat untuk pengguna.

Model dibangun dengan layer berikut:
- Embedding Layer
Fungsi: Layer ini mengubah input ID (user dan place) menjadi representasi vektor berdimensi tetap (embedding). Representasi ini memungkinkan model memahami hubungan tersembunyi antara pengguna dan tempat wisata.
- Bias Embedding
Fungsi: Layer ini menambahkan bias khusus untuk setiap pengguna dan tempat.

Parameter yang digunakan dalam model ini adalah:

users_count: jumlah user yang akan jadi input dimension pada user embedding, tepatnya sebagai jumlah elemen dari vocabulary atau kata-kata yang digunakan dalam input data
place_count: jumlah tempat yang akan jadi input dimension pada tempat embedding, tepatnya sebagai jumlah elemen dari vocabulary atau kata-kata yang digunakan dalam input data
embedding_size: ukuran embedding akan jadi output dimension pada user embedding dan tempat embedding, yaitu jumlah fitur yang dihasilkan oleh Embedding layer, yang merupakan hasil pengurangan dimensi dari input data.
Embedding layer ini akan mengubah representasi numerik dari input data menjadi representasi vektor yang lebih bermakna dan dapat dipahami oleh model machine learning.

#### Selanjutnya dilakukan proses kompilasi atau compile dengan:
  - binary crossentropy loss function: loss function untuk menghitung loss pada model klasifikasi biner.
  - adam optimizer: algoritma optimisasi yang digunakan untuk mengupdate bobot pada model machine learning secara efisien
  - metrik RMSE (Root Mean Square Error): metrik yang digunakan untuk mengukur seberapa jauh hasil prediksi dari model dari nilai aktual. RMSE dihitung dengan mencari rata-rata dari kuadrat error yang diakumulasikan dari seluruh data.

#### RMSE Formula

Rumus **RMSE (Root Mean Squared Error)** untuk menghitung kesalahan prediksi:
   Nilai RMSE dari sistem rekomendasi dengan pendekatan _collaborative filtering_ adalah 0.3384 pada _Training RMSE_, dan 0.3512 pada _Validation RMSE_. Sedangkan untuk nilai _training loss_ sebesar 0.6849, dan _validation loss_ sebesar 0.6958.
   
#### Menambahkan callback EarlyStopping yang akan menghentikan training jika tidak ada peningkatan selama 5 epochs.
Epoch memastikan model memiliki cukup waktu untuk belajar pola dalam data secara bertahap.

#### Visualisasi grafik data training dan testing untuk masing-masing metrik Root Mean Square Error dan loss function.

#### Uji Coba
- Melakukan uji coba atau tes rekomendasi tempat yang diberikan. Namun perlu dikertahui terlebih dahulu untuk variabel khusus orang yang belum pernah mengunjungi tempat tersebut (belum memberikan rating) dengan place_not_rated.
- Melakukan pengujian prediksi hasil rekomendasi tempat berdasarkan nama tempat dan kategori.

Berdasarkan hasil rekomendasi tempat di atas, dapat dilihat bahwa sistem rekomendasi mengambil pengguna acak , lalu dilakukan pencarian tempat dengan rating terbaik dari user tersebut.

- Taman Lapangan Banteng: Taman Hiburan
- Wisata Kaliurang: Cagar Alam
- Taman Buah Surabaya: Taman Hiburan
- Taman Ekspresi Dan Perpustakaan: Taman Hiburan
- Monumen Tugu Pahlawan: Budaya

Selanjutnya, sistem akan menampilkan 10 daftar tempat yang direkomendasikan berdasarkan kategori yang dimiliki terhadap data pengguna acak tadi. Dapat dilihat bahwa sistem merekomendasikan beberapa tempat dengan kategori yang sama, seperti

- Kampoeng Rawa: Cagar Alam
- Masjid Nasional Al-Akbar: Tempat Ibadah
- Keraton Surabaya: Budaya
- Monumen Jalesveva Jayamahe: Budaya
- Atlantis Land Surabaya: Taman Hiburan
- Taman Mundu: Taman Hiburan
- Museum Mpu Tantular: Budaya
- Taman Air Mancur Menari Kenjeran: Taman Hiburan
- Taman Flora Bratang Surabaya: Taman Hiburan
- Gereja Perawan Maria Tak Berdosa Surabaya: Tempat Ibadah

## 6. Evaluation

Untuk mengukur bagaimana performa dari model yang telah dibuat, diperlukannya metriks evaluasi untuk mengevaluasi model sistem rekomendasi film. Berikut adalah rincian metrik yang digunakan untuk tiap pendekatan:

- `Content-Based Filtering` : `Precision`
- `Collaborative Filtering` : `Root Mean Squared Error`

Berikut ini adalah penjelasan mengenai setiap metrik beserta hasil perhitungan metrik dari model yang telah dibuat :

- `Content-Based Filtering` : `Precision`
  - `Precision`
  
    Presisi merupakan ukuran yang menilai efektivitas model klasifikasi dalam mengidentifikasi label positif. Ukuran ini merupakan perbandingan antara jumlah prediksi yang benar-benar positif dengan keseluruhan hasil yang diprediksi sebagai positif, termasuk yang sebenarnya negatif.

    Berikut adalah formula dan cara kerja dari `Precision` :
    
    - **Formula**

       ![gambar_2](https://github.com/user-attachments/assets/fc8d32e3-a801-488d-b6a0-3f66c2907a5c)

_rumus menggunakan gambar karena terdapat kendala dalam menggunakan latex formula_

Di mana:

      TP = True Positive (rekomendasi yang sesuai)
      FP = False Positive (rekomendasi yang tidak sesuai)


    - **Cara Kerja**

    precision = 5/(5+0) = 100 %

    Dengan begitu, diperoleh nilai _precision_ sebesar **100%**.
      
    - Penjelasan Hasil `Precision` dari model `Content-Based Learning`
    - Fungsi dari `calculate_precision` digunakan untuk perhitungan Presisi berdasarkan formula Presisi
 
      ```python
      # Calculate precision
      def place_recommendations(place_name, similarity_data=cosine_sim_df, items=places[['Place_Name', 'Category']], k=5):
        index = similarity_data.loc[:,place_name].to_numpy().argpartition(range(-1, -k, -1))
        closest = similarity_data.columns[index[-1:-(k+2):-1]]
        closest = closest.drop(place_name, errors='ignore')
        return pd.DataFrame(closest).merge(items).head(k)
      ```
 
      Function utama yang digunakan untuk menghitung skor `Precision` dari model Content-Based Filtering telah berhasil dibuat.

      Berdasarkan hasil rekomendasi tempat wisata dengan pendekatan _content-based filtering_ dapat dilihat bahwa hasil yang diberikan oleh sistem rekomendasi berdasarkan tempat wisata **Pantai Parangtritis** dengan kategori **Bahari**, menghasilkan 5 rekomendasi judul tempat wisata yang tepat. Tetapi secara keseluruhan sistem merekomendasikan tempat wisata dengan tepat.    

    
- `Colaborative Filtering` : `Root Mean Squared Error`
  - `Root Mean Squared Error`
    
    Root Mean Square Error (RMSE) adalah metrik yang sering digunakan dalam machine learning untuk mengukur seberapa baik sebuah model prediktif dapat memperkirakan nilai yang sebenarnya. RMSE merupakan akar kuadrat dari rata-rata perbedaan kuadrat antara nilai yang diprediksi oleh model dan nilai yang sebenarnya (nilai aktual).

    Berikut ini adalah formula dan cara kerja dari `Root Mean Squared Error` :

    - **Formula**

   ![gambar_3](https://github.com/user-attachments/assets/8323ec31-9925-41c3-95a7-1a1f08210a3f)

Dimana:

n = jumlah dataset
i = urutan data dalam dataset
y_i = nilai yang sebenarnya
y_pred_i = nilai prediksi terhadap i

