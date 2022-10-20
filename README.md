# Laporan Proyek Machine Learning - Akh.Faris Farhan Zaima

## Latar Belakang

Transportasi adalah salah satu bagian dari kehidupan sehari hari manusia. Berbagai macam transportasi yang tersedia mulai dari transportasi darat, laut, dan udara.Tujuan dari dibuatnya transportasi adalah memudahkan seseorang berpindah ke suatu tempat dengan waktu yang sesingkat mungkin. Ada banyak jenis transportasi yang digunakan, mulai dari sepeda, mobil, kapal laut dan lain lain. Pesawat merupakan salah satu transportasi umum yang sering digunakan oleh banyak orang, terutama bagi orang yang ingin pergi ke suatu tempat yang jauh dalam waktu yang cepat. Dengan pelayanan tersebut, pastinya ada harga yang perlu dibayarkan untuk mendapatkan pelayanan tersebut. Terdapat banyak parameter yang mempengaruhi tinggi rendahnya harga tiket untuk pesawat , mulai dari jarak tempuh, seberapa mampu untuk terbang, teknologi yang digunakan dan banyak hal lainnya. Harga harga tersebut sudah diprediksikan dan ditentukan oleh maskapai dan pihak negara. 

Sebagai perusahaan maskapai perlu melakukan prediksi harga melalui data data yang sudah ada. Analisa harga pasar melalui prediksi ini sangat penting agar sebuah perusahaan mampu berkembang di tengah persaingan maskapai-maskapai yang lain. Dengan demikian, setiap perusahaan harus mampu mempertahankan kelangsungan hidup perusahaan tersebut sebagai organisasi.(Tjiptono,2008). Prediksi ini dilakukan dengan mendapatkan data dari berbagai media yang kemudian dilakukan prediksi dengan berbagai algoritma seperti KNN,RandomForest dan AdaBoosting. Dari hasil prediksi tersebut kemudian dilakukan evaluasi agar didapatkan hasil prediksi yang terbaik.


## Business Understanding

Pada bagian ini, kamu perlu menjelaskan proses klarifikasi masalah.
Sebelum menjalankan proses prediksi, adapun rumusan masalah yang disusun antara lain :

Bagian laporan ini mencakup:

### Problem Statements
- Apakah model yang dibuat dapat memprediksi dengan baik ?
- Algoritma manakah yang dapat memprediksi lebih baik ?
- Fitur apa yang paling berpengaruh terhadap harga tiket ?

### Goals
Adapun tujuan disusun antara lain :
- Mengetahui model dapat memprediksi dengan baik melalui proses prediksi dan scoring
- Mengetahui algoritma terbaik dengan melakukan perbandingan terhadap nilai prediksi dari semua algoritma yang ada
- Penggunaan algoritma KNN, Random Forest dan Boosting sebagai algoritma untuk mencapai solusi  yang diinginkan
- Mendapatkan fitur yang paling berpengaruh terhadap harga tiket

## Data Understanding

Dataset yang digunakan adalah dataset yang berisikan data data penerbangan berikut dengan harga untuk setiap penerbangan. Dataset ini merupakan data penerbangan pesawat di 6 kota besar di India yang diperoleh dari situs Kaggle [Flight Price Prediction](https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction). Data tersebut telah dibersihkan oleh pemilik akun kaggle SHUBHAM BATHWAL. Dataset terdiri atas 300261 baris data dengan 11 variabel. 

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

### Variabel-variabel pada Flight Price Prediction dataset adalah sebagai berikut:
- Airlines: Nama maskapai penerbangan yang tersimpan dalam kolom airlines
- Flight:  Informasi mengenai kode penerbangan pesawat
- Source City: Kota asal penerbangan lepas landas. 
- Departure Time: Keterangan waktu dimana pesawat lepas landas (Pagi, malam, dll)
- Stops:  Jumlah perhentian antara kota asal dan kota tujuan.
- Arrival Time: Keterangan waktu dimana pesawat tiba (Pagi, malam, dll)
- Destination City: Kota tempat penerbangan tiba
- Class: Kategori pesawat
- Duration: Jumlah keseluruhan waktu yang dibutuhkan selama perjalanan dalam satuan jam 
- Day Left: jumlah antara hari pemberangkatan dan hari ini
- Price : informasi harga tiket pesawat terbang.

Dari dataset, diketahui terdapat  11 variabel (fitur). Selanjutnya pemahaman data bisa kita lakukan dengan melihat informasi tipe data, keunikan setiap colum dengan teknik countplot dari seaborn seperti dibawah ini:
![Fitur Airline](https://github.com/akhfarisfz/MLTerapan_1/blob/cfc935685dfae2f8480395d0de8435ca66ccbe12/Airlines.png)

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.

