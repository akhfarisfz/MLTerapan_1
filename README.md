# Laporan Proyek Machine Learning - Akh.Faris Farhan Zaima

## Domain Proyek

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

![Gambar Fitur Airline](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Airlines.png?token=GHSAT0AAAAAAB2EQMNT45MME3ZUOQSEWJK6Y2Q3BUQ)

Fitur Airline

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/Arrival%20Time.png)

Fitur Arrival Time

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/Departure%20Time.png)

Fitur Departure Time

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/Destination%20City.png)

Fitur Destination City

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/Source%20City.png)

Fitur Source City

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/Stops.png)

Fitur Stops

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/Prive.png)

Fitur Price 

Selain itu, Visualisasi data price dan day left

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/Day_left.png)

Day left vs Price

visualisasi dilakukan antara fitur airline dengan price

![Gambar](https://github.com/akhfarisfz/MLTerapan_1/blob/88bd95ae0fd2f0e77669579ad452a7266f0c2c72/price%20vs%20airline.png)

Price vs airlines

Visualisasi data ditampilkan menggunakan teknik countplot dimana menghitung setiap value unik pada fitur tujuan. Tujuannya visualisasi data ini adalah selain mendapatkan visual secara umum, dapat digunakan untuk melihat apakah ada value yang janggal pada data bertipe kategori. Visualisasi pada data yang bertipe numerik dilakukan dengan berbagai plot seprti pie plot, line plot, dan lain lain tujuannya untuk mengetahui hubungan antar fitur sehingga mendapatkan gambaran umum bagaimana hubungan antar fitur  sebelum dicari kebenarannya melalui data preparation.

Selanjutnya adalah Eksploratory Data Analysis. EDA digunakan untuk "membersihkan" data dari data data yang tidak valid sehingga tidak mempengaruhi efisiensi hasil nantinya. EDA dilakukan pada data dengan cara  mengetahui variabel data dengan fungsi info() dan fungsi describe(). Selanjutnya menghilangkan missing value, outlier, dan melakukan filtering dengan InterQuartile.
Teknik Univariate dan Multivariate digunkan untuk melihat secara numerik bagaimana hubungan antar fitur sehingga mendapatkan data yang sudah "bersih".


## Data Preparation

Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.
Data preparation merupakan tahap dimana kita melakukan konversi data sampai cocok dengan proses pemodelan selanjutnya. Adapun teknik yang digunakan antara lain transofrmasi data dengan encoding data, feature engineering pembagian data train dan test menggunakan fungsi train_test_split dari library sklearn, dan  Standarisasi menggunakan StandardScaller. 

Encoder menggunakan teknik one-hot-encoding tujuannya melakukan tranformasi data bertipe kategori menjadi value numerik(1,2,3,..). Teknik ini diperlukan agar selanjutnya fitur ini bisa masukkan ke dalam data test dan train sehingga mempengaruhi model nantinya.

Metode pembagian data menggunakan fungsi train_test_split  digunakan untuk evaluasi performa pada model machine learning. Metode ini akan membagi dataset0 menjadi dua bagian bagian yang digunakan untuk training data dan untuk testing data. Pada proyek ini, digunakan proporsi training:test sebesar 66:33.

Adakalanya pada dataset, fitur memiliki rentang value yang berbeda beda. Sehingga algoritma perlu memakan waktu yang cukup lama untuk memrposes model. Untuk memudahkan pemrosesan model algoritma adalah menyederhanakan data agar mendekati distribusi normal. Standasasi membantu agar fitur diubah menjadi bentuk yang lebih mudah diproses oleh algoritma 

## Modeling

Dalam proses pemodelan digunkakan beberapa model yang digunakan. Model model yang digunakan disesuaikan dengan data yang digunakan. Tahapan pada model yang dilakukan pada data train dan test antara lain :
- K Nearest-Neighbour (KNN), sebuah model yang mengklasifikasikan objek berdasarkan jarak yang paling dekat. KNN memiliki kelebihan mudah digunakan karena sederhana namun kekurangannya akurasi dalam mengklasifikasi kan fitur yang tidak relevan dan bias lainnya. Model ini cocok dengan proyek ini karena dataset yang digunakan masih sederhana mendapatkan hasil prediksi yang paling baik. Pada modeling ini menggunakan data mean square error dari data train dan test.KNN yang dipilih menggunakan parameter k=10 dan metric Euclidean
- RadomForest,  merupakan pengembangan dari metode CART,yaitu dengan menerapkan metode bootstrap aggregating (bagging) dan random feature selection(Samudra,2019).Tujuannya adalah mengklasifikasikan data dalam jumlah besar.Cara kerjanya adalah meningkatkan keacakan pada model sembari meningkatkan tree. Random forest memiliki kelebihan dapat mendeteksi dan membersihkan noise dan missing value.Parameter yang digunakan pada proyek ini antara lain 
    - n_estimator merupakan jumlah pohon di struktur forest.Pada proyek, menggunakan set 50 trees(pohon)
    - max_depth: kedalaman tree(pohon). Pada proyek ini di set max depth=16
    - random_state: random generator. Pada proyek ini digunakan bernilai 55
    - n_jobs: Bernilai -1 artinya semua proses berjalan secara paralel.
- AdaBoost adalah algoritma ensemble yang memanfaatkan bagging dan boosting untuk mengembangkan peningkatan akurasi prediktor(Kurniawati,2021).Adaboost memiliki kelebihan memiliki algoritma yang sederhana dan membutuhkan waktu yang singkat sehingga cocok dengan data proyek yang digunakan.Ada beberapa parameter yang digunakan antara lain:
    - learning_rate: bobot yang diterapkan pada setiap regressor.Ditentukan learning rate sebesar 0.05
    - random_state: random generator. Pada proyek ini digunakan bernilai 55 

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Tahap evaluasi dari dari proyek ini menggunakan metrik MSE (Mean Squarred Error) dalam proses dari semua model yang digunakan. Metrik ini menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi.MSE didefinisikan sebagai berikut

![MSE](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/c71920a263e03e704769a5c4c8f840235e0d8492/MSE.png?token=GHSAT0AAAAAAB2EQMNTWHMR6XEMZFORLJ2CY2Q27FA)

Menggunakan MSE, didapatkan hasil seperti berikut :
![Hasil prediksi](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Summary_1.png?token=GHSAT0AAAAAAB2EQMNTUCWXBI34PKPT3T5GY2Q3IGA)

![Hasil prediksi bar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Prediction_summary.png?token=GHSAT0AAAAAAB2EQMNSEK2JWGJJCSQKDUUAY2Q3GAA)

Dari data di atas 
Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

Referensi :

- Bathwal,Shubham.2022.https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction(diakses pada 20 Oktober 2022)
- YASMIN54301.2022.https://www.kaggle.com/code/yasmin54301/flight-price-prediction(diakses pada 20 Oktober 2022)
- Samudra,Agenda Yudha.2019.PENDEKATAN RANDOM FOREST UNTUK MODEL PERAMALAN HARGA TEMBAKAU RAJANGAN DI KABUPATEN TEMANGGUNG


**---Ini adalah bagian akhir laporan---**


