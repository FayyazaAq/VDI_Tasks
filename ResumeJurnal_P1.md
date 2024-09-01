# Making Data Visualization More Efficient And Effective : A Survey

by: Xuedi Qin · Yuyu Luo · Nan Tang · Guoliang Li

## Pendahuluan
Visualisasi data terbukti ampuh untuk menampilkan cerita-cerita menarik dari sebuah data kepada manusia yang lebih tertarik pada visual. Melalui visualisasi data, ringkasan dari data yang sangat banyak dapat ditampilkan dengan baik sehingga memudahkan dalam melakukan interpretasi analisis data.

### Alur Visualisasi Data
1. **Impor Data**.
2. ***Data Preparation***.
3. **Manipulasi Data** untuk menyeleksi data yang akan divisualisasikan.
4. ***Mapping*** untuk memetakan data yang telah diseleksi sehingga membentuk geometri beserta atribut yang digunakan.
5. ***Rendering*** untuk mengubah data geometri menjadi representasi visual.

Dari alur yang telah disebutkan, ada 3 aturan yang dapat membuat visualisasi data menjadi efisien dan efektif.

1. **Spesifikasi Visualisasi**. Menyediakan banyak cara agar para pengguna bisa mendapatkan apa yang diinginkan. Ada dua alasan mengapa spesifikasi visualisasi dimasukkan dalam aturan ini, yaitu :
    1. ***Self-completeness*** atau kelengkapan diri. Penting untuk mengetahui cara menghasilkan visualisasi yang baik.
    2. **Perspektif desain bahasa**. Terutama dalam menyediakan komponen *Mapping*.
2. **Pendekatan Efisien untuk Visualisasi Data**. Proses pembuatan visualisasi data haruslah efisien dan terskala, terlebih untuk *Data Manipulation* dan *Mapping*.
3. **Rekomendasi Visualisasi  Data**. Sangat penting bagi sistem visualisasi untuk dapat dengan cermat memandu pengguna dengan menyediakan beberapa rekomendasi.

## Spesifikasi Visualisasi 

### Spesifikasi Visualisasi Data

Bahasa visualisasi data terbagi menjadi 3 bagian.

1. **Data** yang perlu/akan divisualisasikan.
2. **Tanda** atau isyarat visual yang merepresentasikan data.
3. **Pemetaan** atau *Mapping* sesuai tanda yang berkaitan.

### Kategori Bahasa Visualisasi Data

Bahasa yang biasanya digunakan untuk visualisasi data bergantung pada ekspresi yang ada. Kelihatannya, semakin rendah suatu level bahasa maka semakin ekspresif, begitu pun sebaliknya.

1. ***Low-level Languages*** merujuk pada bahasa dimana penggunanya harus menspesifikkan setiap elemen pemetaan. Contohnya : Prefuse, Flare, Protvis, D3, Vega, dan Reactive Vega.
2. ***High-level Languages*** adalah bahasa yang merangkum detail konstruksinya seperti pada fungsi pemetaan, dll. Contohnya : ggplot2, Vega-Lite, Altair, Echarts, VizQL, dan ZQL.

### Operasi Visual Basis GUI

Cara yang lebih mudah digunakan untuk memberikan spesifikasi adalah dengan mengikuti "prinsip manipulasi langsung", sebuah konsep yang biasa digunakan dalam aspek interaksi manusia-komputer. Contohnya : Tableu, Excel, Keshif, iVisDesigner, Qlik, Lyra, Google Sheets, Amazon Quicksight, Microsoft Power BI, Data Illustrator, dan Google Fushion Tables.

#### Visualisasi Data Interaktif
Ide awal visualisasi data interaktif ini adalah banyaknya kasus dimana penggunan perlu melakukan penyempurnaan (seperti menambah, menghapus, dll) pada visualisasi yang sedang dieksplorasi sehingga didapatkan visualisasi yang sesuai dengan keinginan dalam proses eksplorasi
Ada 2 langkah penyempurnaan kueri untuk membuat visualisasi multidimensi, yaitu :
1. **Penyempurnaan Kueri Bertahap** Polaris dan Tableu menyediakan templat bagan multidimensi. 
2. ***Faceted Navigation*** digunakan untuk membantu pengguna menjelajahi ruang desain visualisasi.

> Alat interaktif basis GUI pada dasarnya digunakan untuk membuat prototype dengan cepa atau untuk menemukan visualisasi yang dapat digunakan. Nantinya, *lo-level languages* akan digunakan untuk melakukan penyempurnaan atau untuk menerapkan kembali visualisasi yang diinginkan.

### Perincian Kurang Spesifik
Visualisasi akan menjadi tidak berguna jika tidak dapat memberikan wawasan dari data. Dalam banyak kasus, pengguna juga tidak betul-betul memahami tiap aspek dalam data karena data yang digunakan sangat besar atau seringnya perubahan terjadi dalam data tersebut. Maka dibutuhkan suatu persyaratan yang mendukung perincian yang kurang spesifik. 
Pengguna hanya dapat menyediakan beberapa "petunjuk".
1. ***Reference-based***. Pengguna menyediakan suatu referensi visualisasi sebagai benih lalu sistem akan menyarankan visualisasi yang sesuai dengan referensi
2. ***Keyword-based***. APT akan menerima target tampilan data yang diinginkan oleh pengguna kemudian merekomendasikan visualisasi yang mungkin akan memenuhi target.
3. ***Natural Language-based***. Basis ini memperhatikan konteks masukan dari user dan status sistem dalam siklus eksplorasi data, bukan seperti pada petunjuk *keyword-based*.

## Pendekatan Efisien untuk Visualisasi Data 

Daur hidup visualisasi data selalu interaktif. Tetapi, menyediakan visualisasi yang tepat tidak selalu dapat dilakukan karena ukuran data yang besar dan kompleksitas kueri yang tinggi sehingga 'visualisasi data perkiraan' yang memberikan visualisasi cepat menjadi visualisasi yang ideal untuk kasus ini. Lagi, daripada memberikan visualisasi perkiraan sekali pakai, visualisasi data progresif secara bertahap menyempurnakan hasil.

### Visualisasi Data Akurat

#### Penerjemahan Kueri
Cara yang wajar untuk menggunakan sistem-sistem yang telah matang (DBMS) adalah dengan menerjemahkan kueri visualisasi ke dalam kueri yang diterima oleh sistem tersebut. Dengan membuat pemetaan antara bahasa visualisasi primitif dan bahasa SQL, kita dapat mengubah target bahasa visualisasi ke kueri SQL.

#### Mengintegrasikan Sistem Visualisasi dengan DBMS
Ada beberapa kekurangan dalam penerjemahan kueri. Salah satunya adalah banyak fungsi yang berulang sehingga teknik optimasi tidak berpadu dengan berbagai asumsi dan performa pada server dan klien. Hal ini menyebabkan pengembang kebingungan memilih teknik optimasi yang sesuai.
Masalah lainnya adalah masalah yang dipisahkan sulit untuk dipelihara, diperluas, dan dioptimalkan untuk visualisasi interaktif yang memerlukan penerbitan kueri secara terus-menerus untuk memodifikasi visualisasinya. Cara yang menjanjikan untuk memecahkan masalah tersebut adalah dengan menggabungkan pengambilan data dan melakukan *rendering* bersama untuk mempercepat proses pembuatan visualisasi. Upaya penelitian dyang dilakukan adalah Sistem Manajemen Visualisasi Data (DVMS).

#### Penyimpanan Kolom
Mungkin terdapat perbedaan yang besar dengan aplikasi OLAP karena dalam hal visualisasi data, pengguna biasanya hanya tertarik pada beberapa kolom.

#### Indeks 
Indeks yang digunakan untuk meningkatkan kinerja pencarian pada dasarnya adalah dengan mengurangi jumlah catatan/baris dalam tabel yang perlu diperiksa.

#### Komputasi Paralel 
Komputasi paralel digunakan untuk melakukan proses kueri dalam sistem visualisasi data

#### Prediksi dan *Prefetching*
Pengguna dapat memperoleh visualisasi berikutnya dengan mengubah parameter visualisasi saat ini atau memperbesar atau memperkecil tampilan untuk memperoleh informasi terperinci, dll. Memperkirakan data berikut yang mungkin diminati pengguna, lalu melakukan prapengambilan/penyimpanan data yang dapat digunakan pada langkah berikutnya selama eksplorasi dapat mempercepat proses.
Teknologi prefetch dan prediksi terbagi menjadi dua jenis, yaitu :
1. Visualisasi yang Sedang Dieksplorasi.
2. Data Historis.

