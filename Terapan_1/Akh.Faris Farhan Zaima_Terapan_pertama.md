# Laporan Proyek Machine Learning - Akh.Faris Farhan Zaima

## Domain Proyek

Transportasi adalah salah satu bagian dari kehidupan sehari hari manusia. Berbagai macam transportasi yang tersedia mulai dari transportasi darat, laut, dan udara.Tujuan dari dibuatnya transportasi adalah memudahkan seseorang berpindah ke suatu tempat dengan waktu yang sesingkat mungkin. Ada banyak jenis transportasi yang digunakan, mulai dari sepeda, mobil, kapal laut dan lain lain. Pesawat merupakan salah satu transportasi umum yang sering digunakan oleh banyak orang, terutama bagi orang yang ingin pergi ke suatu tempat yang jauh dalam waktu yang cepat. Dengan pelayanan tersebut, pastinya ada harga yang perlu dibayarkan untuk mendapatkan pelayanan tersebut. Terdapat banyak parameter yang mempengaruhi tinggi rendahnya harga tiket untuk pesawat , mulai dari jarak tempuh, seberapa mampu untuk terbang, teknologi yang digunakan dan banyak hal lainnya. Harga harga tersebut sudah diprediksikan dan ditentukan oleh maskapai dan pihak negara. 

Sebagai perusahaan maskapai perlu melakukan prediksi harga melalui data data yang sudah ada. Analisa harga pasar melalui prediksi ini sangat penting agar sebuah perusahaan mampu berkembang di tengah persaingan maskapai-maskapai yang lain. Dengan demikian, setiap perusahaan harus mampu mempertahankan kelangsungan hidup perusahaan tersebut sebagai organisasi [1]. Prediksi ini dilakukan dengan mendapatkan data dari berbagai media yang kemudian dilakukan prediksi dengan berbagai algoritma seperti *KNN* ,*RandomForest* dan *AdaBoosting*. Dari hasil prediksi tersebut kemudian dilakukan evaluasi agar didapatkan hasil prediksi yang terbaik.


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
- Mengetahui model dapat memprediksi sebuah model
- Mengetahui algoritma terbaik dengan melakukan perbandingan terhadap nilai prediksi dari semua algoritma yang ada
- Mendapatkan fitur yang paling berpengaruh terhadap harga tiket


## Data Understanding

Dataset yang digunakan adalah dataset yang berisikan data data penerbangan berikut dengan harga untuk setiap penerbangan. Dataset ini merupakan data penerbangan pesawat di 6 kota besar di India yang diperoleh dari situs Kaggle [Flight Price Prediction](https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction)[2]. Dataset terdiri atas 300261 baris data dengan 11 variabel. 

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

Fitur Airline

![Gambar Fitur Airline](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Arrival%20Time.png)

Gambar 1.Persentase setiap Airplane pada dataset

Fitur Arrival Time

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Arrival%20Time.png)

Gambar 2.Countplot fitur Arrival Time

Fitur Departure Time

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Departure%20Time.png)

Gambar 3. Countplot Departure Time

Fitur Destination Fitur City

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Destination%20City.png)

Gambar 4. Countplot Fitur Destination City

Fitur Source City

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Source%20City.png)

Gambar 5. Countplot Fitur Source City

Fitur Stops

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Stops.png)

Gambar 6. Countplot Fitur Stops

Fitur Price 

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Prive.png)

Gambar 6. Countplot Fitur Price

Selain itu, Visualisasi data price dan day left

Day left vs Price

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Day_left.png)

Gambar 7. Plot antara Fitur Day Left dan Price

Price vs airlines

![Gambar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/price%20vs%20airline.png)

Gambar 8. Barplot antara Fitur Price dan Airline

Visualisasi data ditampilkan menggunakan teknik countplot dimana menghitung setiap value unik pada fitur tujuan. Tujuannya visualisasi data ini adalah selain mendapatkan visual secara umum, dapat digunakan untuk melihat apakah ada value yang janggal pada data bertipe kategori. Visualisasi pada data yang bertipe numerik dilakukan dengan berbagai *plot* seprti *pie plot*, *line plot*, dan lain lain tujuannya untuk mengetahui hubungan antar fitur sehingga mendapatkan gambaran umum bagaimana hubungan antar fitur  sebelum dicari kebenarannya melalui data preparation.

Selanjutnya adalah Eksploratory Data Analysis. EDA digunakan untuk "membersihkan" data dari data data yang tidak valid sehingga tidak mempengaruhi efisiensi hasil nantinya. EDA dilakukan pada data dengan cara  mengetahui variabel data dengan fungsi info() dan fungsi describe(). Selanjutnya menghilangkan *missing value*, *outlier*, dan melakukan *filtering* dengan *InterQuartile*.
Teknik *Univariate* dan *Multivariate* digunkan untuk melihat secara numerik bagaimana hubungan antar fitur sehingga mendapatkan data yang sudah "bersih".Adapun berikut ini adalah hasil *outlier* yang dilakukan pada beberapa fitur :

![Gambar Outlier pada Price](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Outlier_price.png)

Gambar 9. Pengecekan *Outlier* pada *Price*

![Gambar Outlier pada duration](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/duration.png)


Gambar 10.Hasil pengecekan *outlier* pada fitur *duration*

Dan berikut adalah hasil histogram dari Multivariate Data:

![Histogram](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Histogram_2.png)

Gambar 11.Histogram dari data numerik

## Data Preparation

Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.
*Data preparation* merupakan tahap dimana kita melakukan konversi data sampai cocok dengan proses pemodelan selanjutnya. Adapun teknik yang digunakan antara lain:

- transofrmasi data dengan *encoding data*
- *Feature engineering* pembagian data *train* dan *test* menggunakan fungsi train_test_split dari library sklearn,
- Standarisasi menggunakan StandardScaller. 

Perlakuan pada dataset ini dilakukan dengan teknik seperti berikut:

- Encoder menggunakan teknik *one-hot-encoding* tujuannya melakukan tranformasi data bertipe kategori menjadi value numerik(1,2,3,..). Teknik ini diperlukan agar selanjutnya fitur ini bisa masukkan ke dalam data test dan train sehingga mempengaruhi model nantinya.
- Metode pembagian data menggunakan fungsi train_test_split  digunakan untuk evaluasi performa pada model machine learning. Metode ini akan membagi *dataset* menjadi dua bagian bagian yang digunakan untuk training data dan untuk testing data. Pada proyek ini, digunakan proporsi training:test sebesar 80:20.
- Adakalanya pada dataset, fitur memiliki rentang value yang berbeda beda. Sehingga algoritma perlu memakan waktu yang cukup lama untuk memrposes model. Untuk memudahkan pemrosesan model algoritma adalah menyederhanakan data agar mendekati distribusi normal. Standasasi membantu agar fitur diubah menjadi bentuk yang lebih mudah diproses oleh algoritma 

## Modeling

Dalam proses pemodelan digunkakan beberapa model yang digunakan. Model model yang digunakan disesuaikan dengan data yang digunakan. Tahapan pada model yang dilakukan pada data train dan test antara lain :
- K Nearest-Neighbour (KNN), sebuah model yang mengklasifikasikan objek berdasarkan jarak yang paling dekat. KNN memiliki kelebihan mudah digunakan karena sederhana namun kekurangannya akurasi dalam mengklasifikasi kan fitur yang tidak relevan dan bias lainnya. Model ini cocok dengan proyek ini karena dataset yang digunakan masih sederhana mendapatkan hasil prediksi yang paling baik. Pada modeling ini menggunakan data mean square error dari data train dan test.KNN yang dipilih menggunakan parameter k=10 dan metric Euclidean
- RadomForest,  merupakan pengembangan dari metode CART,yaitu dengan menerapkan metode bootstrap aggregating (bagging) dan random feature selection [3] .Tujuannya adalah mengklasifikasikan data dalam jumlah besar.Cara kerjanya adalah meningkatkan keacakan pada model sembari meningkatkan tree. Random forest memiliki kelebihan dapat mendeteksi dan membersihkan noise dan missing value.Parameter yang digunakan pada proyek ini antara lain 
    - n_estimator merupakan jumlah pohon di struktur forest.Pada proyek, menggunakan set 50 trees(pohon)
    - max_depth: kedalaman tree(pohon). Pada proyek ini di set max depth=16
    - random_state: random generator. Pada proyek ini digunakan bernilai 55
    - n_jobs: Bernilai -1 artinya semua proses berjalan secara paralel.
- Adaptive boosting (adaboost) merupakan salah satu dari beberapa varian pada algoritma boosting [4].Adaboost memiliki kelebihan memiliki algoritma yang sederhana dan membutuhkan waktu yang singkat sehingga cocok dengan data proyek yang digunakan.Ada beberapa parameter yang digunakan antara lain:
    - learning_rate: bobot yang diterapkan pada setiap regressor.Ditentukan learning rate sebesar 0.05
    - random_state: random generator. Pada proyek ini digunakan bernilai 55 

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Tahap evaluasi dari dari proyek ini menggunakan metrik MSE (Mean Squarred Error) dalam proses dari semua model yang digunakan. Metrik ini menghitung jumlah selisih kuadrat rata-rata nilai sebenarnya dengan nilai prediksi.MSE didefinisikan sebagai berikut

$$MSE={1\over N}\sum_{i=0}^{N}(y_i -y_{pred_i})^2$$

Keterangan :

N = jumlah dataset

$y_i$ = nilai sebenarnya

$y_{pred}$ = nilai prediksi

Menggunakan MSE, didapatkan hasil seperti berikut :

![Hasil prediksi bar](https://raw.githubusercontent.com/akhfarisfz/MLTerapan_1/main/Gambar/Prediction_summary.png)

Gambar 12. Hasil prediksi menggunakan *bar plot*

Tabel 1.Hasil prediksi algoritma *KNN*,*Random Forest*,dan *AdaBoosting*
|          	|      Test     	|     Train     	|
|----------	|:-------------:	|:-------------:	|
| RF       	| 373650.593225 	| 304105.211741 	|
| KNN      	| 391874.360483 	|  321010.03323 	|
| Boosting 	| 391432.621488 	| 389021.837711 	|


Pada gambar diatas kita mendapatkan hasil dari berbagai algoritma yaitu *KNN*, *Random Forest*, dan *Adaboosting*. Bar berwarna diatas menunjukkan bahwa seberapa besar error yang dihasilkan. Oleh karena itu, kita bisa simpulkan *Random Forest* memiliki error paling rendah dengan angka 373650.593225 untuk *test* dan 304105.211741 untuk *train*. 

Dari data tersebut, kita bisa mendapatkan hasil prediksi dari berbagai algoritma. Hasil prediksi tersebut ditampilkan dari tabel berikut ini:

Tabel 2. Hasil Prediksi 3 Algoritma
|      $$y_{true}$$    	|      RF     	|     KNN     	|     Boosting     	|
|----------	|:-------------:	|:-------------:	|:-------------:	|
| 7426    	|  4859.4	|  5402.3	|4577.9	|

Dari tabel 2 diatas kita bisa simpulkan bahwa algoritma *KNN* memiliki nilai prediksi paling dekat dengan nilai sebenarnya dengan 5402.3 , diikuti oleh algoritma *Random Forest* dengan 4859.4 dan algoritma *Boosting* dengan 4577.9

## Kesimpulan
Dari hasil uji dari dataset Harga tiket dengan tiga algoritma model *machine learning*, kita menggunakan hasil dari *MSE* untuk mendapatkan hasil nilai error dari setiap algoritma. Dari hasil pada tabel 1, kita mendapatkan bahwa algoritma *Random Forest* menghasilkan *error* paling kecil. Selanjutnya dilakukan hasil prediksi yang dibandingkan dengan nilai sebenarnya. Dari tabel 2, kita bisa simpulkan bahwa algoritma *KNN* memiliki nilai prediksi paling dekat dengan nilai sebenarnya dengan angka 5402.3. Sehingga bisa kita simpulkan algoritma yang paling cocok dengan dataset prediksi harga tiket pesawat ini adalah *KNN*.

## Referensi :

[1] Bathwal,Shubham.2022.https://www.kaggle.com/datasets/shubhambathwal/flight-price-prediction(diakses pada 20 Oktober 2022)

[2] Tjiptono, 2008 .Strategi Pemasaran, Edisi III, Yogyakarta : CV. Andi Offset

[3] Samudra,Agenda Yudha.2019.PENDEKATAN RANDOM FOREST UNTUK MODEL PERAMALAN HARGA TEMBAKAU RAJANGAN DI KABUPATEN   TEMANGGUNG

[4] Chezian, D. R. M., & Kumar, K. S. 2014. Support Vector Machine and K-Nearest Neighbor Based Analysis for the Prediction of Hypothyroid.     International Journal of Pharma and Bio Sciences. 5(4): (B) 447- 453. 


**---Ini adalah bagian akhir laporan---**


