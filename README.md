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

