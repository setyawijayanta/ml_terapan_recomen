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
