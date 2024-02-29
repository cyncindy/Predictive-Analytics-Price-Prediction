# Laporan Proyek Machine Learning - Prediksi Harga Rumah (Apartemen)

## Domain Proyek

Keputusan pembelian rumah sangat dipengaruhi oleh harga rumah itu sendiri. Namun, hal tersebut bukan merupakan satu-satunya faktor yang menjadi pertimbangan pembelinya. Keputusan pembelian rumah juga dipengaruhi oleh banyak faktor, termasuk lokasi, kualitas perumahan, kemudahan umum, ciri-ciri struktur rumah, jarak dan lokasi proyek, kemudahan transportasi, keamanan, dan fasilitas yang tersedia [[1](https://journalarticle.ukm.my/14215/1/36213-114170-1-PB.pdf)].

Dalam rangka prediksi harga rumah, telah dirancang sistem yang dapat digunakan untuk melakukan prediksi harga rumah dengan mempertimbangkan berbagai faktor-faktor penentunya. Saat ini, model pengembangan prediksi harga rumah yang paling banyak digunakan adalah model regresi dan model tersebut dapat secara akurat memprediksi harga rumah dengan memasukkan elemen-elemen penentu dari rumah yang dituju [[2](https://ieeexplore.ieee.org/document/9952397)].

## Business Understanding

Berdasarkan proyek yang dikerjakan, tujuan utamanya adalah untuk memprediksi harga rumah dengan akurasi tinggi, dimana ini merupakan hal yang penting bagi penjual yang ingin menentukan harga yang tepat untuk rumah mereka, serta bagi pembeli yang ingin mencari rumah dengan harga yang sesuai dengan kondisi dan kebutuhan mereka.

### Problem Statements

-  Dari hasil observasi berdasarkan dataset, fitur apa saja yang paling mempengaruhi harga rumah?
- Bagaimana cara meningkatkan akurasi model prediksi harga rumah?

### Goals

- Melakukan eksperimen terhadap semua fitur yang tersedia kemudian melihat pengaruh dari masing-masing fitur untuk mengetahui elemen-elemen apa saja yang sangat mempengaruhi hingga kurang mempengaruhi harga rumah.
- Membuat beberapa jenis model dengan algoritma yang berbeda dalam rangka mengetahui model yang paling sesuai untuk diterapkan dalam studi kasus prediksi harga rumah.

### Solution Statements

- Dilakukan Analisis Univariat dan Multivariat, dimana Analisis Univariat ditujukan untuk melakukan eksplorasi data numerik dan data kategorik. Sedangkan dengan dilakukannya Analisis Multivariat, maka dapat dilihat hubungan antar fitur dari setiap elemen yang tersedia. Pada kasus ini, digunakan teknik catplot, pairplot, dan heatmap yang akan menampilkan Correlation Matrix dari setiap elemen-elemen yang dimiliki.
- Melakukan evaluasi performa model dengan metrik evaluasi dan membandingkan performa model untuk penentuan model yang paling sesuai dengan studi kasus.

## Data Understanding

Pada proyek ini, dataset yang digunakan adalah data sekunder yang diperoleh dari Kaggle dengan nama Moscow Housing Price Dataset.

Link Dataset: https://www.kaggle.com/datasets/egorkainov/moscow-housing-price-dataset

Dataset ini memiliki jumlah keseluruhan sebanyak 22.676 jumlah records dengan berbagai variasi dan harga. Variasi yang dimaksud disini adalah faktor-faktor yang mempengaruhi harga rumah yang dapat diukur. Dataset terdiri dari 4 data kategori dan 8 data numerik.

### Variabel-variabel pada dataset adalah sebagai berikut:

- *Price*: Harga apartemen dalam mata uang tertentu. Ini merupakan variabel target utama untuk prediksi.
- *Apartment type*: Jenis apartemen, seperti studio, satu kamar tidur, dua kamar tidur, dan lain-lain.
- *Metro station*: Nama stasiun metro terdekat dari lokasi apartemen.
- *Minutes to metro*: Waktu dalam menit yang diperlukan untuk berjalan kaki dari apartemen ke stasiun metro terdekat.
- *Region*: Wilayah tempat apartemen berada (Moskow atau Oblast Moskow).
- *Number of rooms*: Jumlah total kamar di apartemen, termasuk kamar tidur, ruang keluarga, dan lain-lain.
- *Area*: Luas total apartemen dalam meter persegi.
- *Living area*: Ruang tamu apartemen dalam meter persegi, yaitu area yang dapat digunakan untuk tempat tinggal.
- *Kitchen area*: Luas dapur dalam meter persegi.
- *Floor*: Lantai tempat apartemen berada.
- *Number of floors*: Jumlah total lantai di gedung tempat apartemen berada.
- *Renovation*: Tingkat renovasi apartemen, seperti "tidak ada renovasi", "renovasi kosmetik", "renovasi euro", dan lain-lain.

Dilakukan juga Analisis Univariat dan Analisis Multivariat untuk memahami data lebih lanjut, serta dilakukan pula Visualisasi Data agar informasi pada data dapat dengan mudah dipahami.

Analisis Univariat menganalisis suatu variabel atau data tunggal. Variabel dipelajari secara independen tanpa mempertimbangkan hubungannya dengan variabel lain. Analisis Univariat dapat menemukan sebaran dan kecenderungan data. Berbanding terbalik dengan Analisis Univariat, Analisis Multivariat adalah teknik statistik yang digunakan untuk mengumpulkan dan menganalisis hubungan antara lebih dari dua variabel yang terkait dengan data tersebut. Analisis ini mencakup variabel dependen (Y), yang dipengaruhi oleh satu atau lebih variabel independen (X), atau sebaliknya.

Setelah dilakukan Analisis Univariat dan Multivariat, dilakukan Visualisasi data yang bertujuan untuk menunjukkan perilaku berbagai fitur dalam dataset. Dalam melakukan visualisasi, teknik yang dilakukan adalah menggunakan catplot untuk memplot distribusi data pada data data kategori, pairplot untuk menunjukkan hubungan antar fitur dalam dataset, dan heatmap untuk menunjukkan korelasi antar fitur.

Berikut adalah hasil dari Exploratory Data Analysis (EDA) yang telah dilakukan.

## Univariate Analysis

### Categorical Features

- Fitur Apartment type

![Image 1](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/CatFeatures1.png?raw=true)

Berdasarkan gambar tersebut, diketahui bahwa distribusi data kategori 'Apartment type' memiliki perbandingan jumlah yang berbeda, untuk nlai data 'New building' memiliki jumlah sampel sebesar 8.169 dengan persentase 55.7% dan 'Secondary' memiliki jumlah sampel sebesar 6.493 dengan persentase 44.3%.

- Fitur Region

![Image 2](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/CatFeatures2.png?raw=true)

Data kategori 'Region' juga memiliki nilai yang lebih jauh berbeda antara keduanya yaitu 9.125 sampel untuk 'Moscow' dengan jumlah persentase 62.2%, sedangkan untuk 'Moscow region' memiliki sampel sebesar 5.537 sampel yaitu sebesar 37.8%.

- Fitur Renovation

![Image 3](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/CatFeatures3.png?raw=true)

Terakhir, untuk data kategori 'Renovation' juga memiliki persebaran data yang tidak merata yaitu sebesar 10.577 sampel untuk 'Cosmetic' dengan persentase 72.1%, sedangkan untuk 'European-style renovation' mencapai jumlah 2.222 sampel dan persentase sebesar 15.2%, untuk 'Without renovation' sebesar 1.106 sampel dengan jumlah persentase 7.5%, serta 'Designer' sebanyak 757 sampel dengan persentase 5.2%.

### Numerical Features

![Image 4](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/NumFeatures1.png?raw=true)

Pada gambar diatas, dapat dilihat bahwa data numerik memiliki karakteristik sebagai berikut:

- Rentang data harga rumah paling banyak berada pada angka 1.600 sampai 1.700 yaitu rumah yang berada pada harga 9.000.000 hingga 10.000.000
- Persebaran data yang beragam untuk kategori 'Minutes to metro' dimana data terbanyak yang tersedia adalah rumah dengan rentang jarak 13 menit dari rumah ke metro yaitu sekitar 1.750 data.
- Ruangan terbanyak pada data ini yaitu adalah rumah yang memiliki sebanyak 2 ruangan, dan rumah yang memiliki ruangan paling sedikit adalah rumah dengan 5 ruangan.
- Luas area yang berada pada rentang 40 meter persegi hingga 45 meter persegi yang memiliki jumlah data terbanyak yaitu mencapai lebih dari 1.200 data dan semakin luas area nya maka semakin sedikit data yang dimiliki.
- Luas living area terbanyak yang memiliki hingga lebih dari 800 data berada pada angka 22 meter persegi hingga 25 mter persegi, dan semakin luas living area nya maka semakin sedikit data yang dimiliki. 
- Luas kitchen area sebesar 10 meter persegi memiliki jumlah data terbanyak yaitu mencapai lebih dari 1.600 data.
- Kebanyakan rumah atau apartemen memiliki lokasi yang terletak di lantai 2 pada bangunan.
- Kebanyakan jumlah total lantai di gedung tempat rumah atau apartemen berada adalah gedung dengan 20 lantai.

## Multivariate Analysis

### Categorical Features

- Rata-rata 'Price' relatif terhadap 'Apartment type'

![Image 5](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/CatFeaturesMulti1.png?raw=true)

Pada fitur 'Apartment type', rata-rata harga berbanding jauh. Apartment type 'Secondary' memiliki harga yang relatif lebih tinggi jika dibandingkan dengan 'New building'. Sehingga, fitur 'Apartment type' memiliki pengaruh yang cukup besar terhadap harga.

- Rata-rata 'Price' relatif terhadap 'Region'

![Image 6](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/CatFeaturesMulti2.png?raw=true)

Untuk fitur 'Region', rata-rata harga juga berbanding jauh. Region 'Moscow region' memiliki harga yang lebih rendah jika dibandingkan dengan region 'Moscow'. Oleh karena itu, fitur 'Region' memiliki pengaruh yang tinggi terhadap harga.

- Rata-rata 'Price' relatif terhadap 'Renovation'

![Image 7](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/CatFeaturesMulti3.png?raw=true)

Dapat dilihat pada fitur 'Renovation', rata-rata harga 'Designer' memiliki nilai tertinggi dan disusul oleh 'Without renovation', dan ketiga 'European-style renovation' dan terakhir 'Cosmetic'. Perbedaan harga diantara beberapa kategori ini yang menyebabkan banyaknya variasi harga berbeda pada fitur 'Renovation' sehingga fitur 'Renovation' memiliki pengaruh yang tinggi terhadap harga.

### Numerical Features

![Image 8](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/NumFeaturesPairPlot().png?raw=true)

Dengan menggunakan fungsi pairplot() dari library seaborn, dapat diketahui relasi pasangan dalam dataset. Berdasarkan gambar, terlihat plot relasi masing-masing fitur numerik pada dataset. Pada pola sebaran data grafik pairplot, fitur 'Area' dan 'Living area' memiliki korelasi dengan fitur 'Price' sedangkan fitur-fitur lainnya terlihat memiliki korelasi yang lemah karena sebarannya tidak membentuk pola.

### Correlation Matrix

![Image 9](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/CorrelationMatrix.png?raw=true)

Correlation Matrix tersebut menunjukkan hubungan antar fitur dalam nilai korelasi. Berdasarkan pengamatan, fitur 'Area', 'Living area', dan 'Number of rooms' merupakan peringkat ketiga terbesar yang memiliki nilai korelasi yang cukup tinggi, yaitu 'Area' sebesar 0.64, 'Living area' sebesar 0.58, dan 'Number of rooms' sebesar 0.41 terhadap fitur target 'Price'. Sementara itu, fitur lainnya memiliki korelasi yang kurang tinggi dan juga negatif sehingga fitur-fitur tersebut dapat dihilangkan atau dieliminasi.

## Data Preparation

Tahap ini merupakan tahap penting dalam proses pengembangan model machine learning sebab ini adalah tahapan dimana proses transformasi data akan dilakukan sehingga menjadi bentuk yang cocok untuk proses pemodelan. Pada tahapan ini dilakukan seleksi fitur, transformasi data, dan reduksi dimensi. 

Beberapa tahap sebelum itu, data terlebih dahulu diimpor dari yang sebelumnya dalam format csv ke dalam dataframe dengan library Pandas yang tersedia dari Python. Setelah itu dilakukan pula penghapusan missing values, penghapusan data duplikat, dan juga menghilangkan outlier.

Missing values pada dataset terdapat pada kolom Minutes to metro sebanyak 7 dan pada kolom Number of rooms sebanyak 3.731. Missing values tersebut kemudian dihilangkan dan menghasilkan 18.939 data. Kemudian, ditemukan pula data duplikat sebanyak 1.339 dan kemudian data duplikat tersebut dihapus dan menghasilkan data sebesar 17.600. Tahap selanjutnya adalah penghapusan outlier dengan metode IQR, dimana caranya adalah mengurangkan nilai Q3 dengan nilai Q1.

Rumusnya adalah sebagai berikut:

![Image 10](https://miro.medium.com/v2/resize:fit:600/format:webp/1*pr8drTK9QYnX-60f3fB5Kw.png)

Q1 adalah kuartil pertama dan Q3 adalah kuartil ketiga.

Setelah dilakukan penghapusan outlier maka total keseluruhan data adalah sebanyak 14.662.

Setelah memperoleh data yang sudah bersih, dilakukan encoding pada data kategorik yaitu untuk kolom Apartment type, Metro station, Region, dan Renovation.

Kemudian dilakukan juga teknik reduksi atau pengurangan dimensi menggunakan teknik yang paling populer yaitu Principal Component Analysis atau PCA. Teknik ini berguna untuk mereduksi dimensi, mengekstraksi fitur, dan mentransformasi data dari "n-dimensional space" ke dalam sistem berkoordinat baru dengan dimensi m, dimana m lebih kecil dari n. Sebelum dilakukan reduksi dimensi, terlebih dahulu dilakukan visualisasi data untuk melihat hubungan antar fitur-fitur yang ada. Berikut dapat dilihat pada gambar dibawah ini.

![Image 11](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/PCA1.png?raw=true)

Dari hasil visualisasi terhadap gambar diatas, dapat diketahui bahwa dari antara tiga fitur yang diamati, hanya 'Area' dan 'Living area' yang memiliki hubungan antar fitur. Maka, kedua fitur tersebut dapat dilakukan reduksi dimensi dengan metode PCA.

Berikut adalah visualisasi kedua fitur 'Area' dan 'Living Area'

![Image 12](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/PCA2.png?raw=true)

Setelah dilakukan reduksi dimensi dan diperoleh proporsi informasi dari ketiga komponen PCs tersebut, diketahui bahwa hasil yang diperoleh berupa array([0.956, 0.044]). Berdasarkan hasil yang diperoleh, sebesar 95.6% informasi pada kedua fitur 'Area' dan 'Living area' terdapat pada PC pertama. Sedangkan sisanya, sebesar 4.4% terdapat pada PC kedua sehingga fitur tersebut akan direduksi dan hanya PC (komponen) pertama saja yang dipertahankan. PC pertama tersebut akan menjadi fitur areas menggantikan kedua fitur 'Area' dan 'Living area'. Fitur tersebut akan dinamakan 'Areas'.

Tahap selanjutnya adalah membagi dataset kedalam dua bagian, yaitu data train dan test untuk dimasukkan ke model, yang rasio pembagian dataset nya adalah 90:10. Berikut adalah hasil pembagian dataset menjadi train dan test:

- Total sampel dari dataset keseluruhan adalah 14.662
- Total sampel dari dataset train adalah 13.195
- Total sampel dari dataset test adalah 1.467

## Modeling

Model yang digunakan dalam menyelesaikan masalah pada studi kasus kali ini adalah SVR, Decision Trees, K-Nearest Neighbor dan Random Forest. Alasan pemilihan algoritma tersebut dalam pembuatan model adalah sebagai berikut:

- Support Vector Regression (SVR) dipilih karena kehandalannya dalam menyelesaikan kasus regresi, yang menghasilkan keluaran berupa bilangan riil dimana konsep algoritma SVR dapat menghasilkan nilai prediksi yang baik karena SVR memiliki kemampuan menyelesaikan masalah overfitting [[3](https://jurnalvariansi.unm.ac.id/index.php/variansi/article/view/13/4)]. Kekurangan algoritma ini adalah penentuan nilai parameter yang tepat sehingga diperlukan algoritma optimasi untuk membantu menentukan nilai parameter SVR yang tepat [[4](https://j-ptiik.ub.ac.id/index.php/j-ptiik/article/view/417)].

- Decision Trees dipilih karena algoritma ini dapat digunakan untuk masalah klasifikasi dan regresi serta membantu mengidentifikasi hubungan di antara titik-titik data [[5](https://www.semanticscholar.org/paper/Applications-of-Decision-Trees-Thomas-Vijayaraghavan/b226d23f7c99713591c700a31dd05b9105b59fbd)]. Kekurangan algoritma ini adalah algoritma ini tidak menyampaikan potensi ketidakpastian dalam klasifikasi, dapat menyebabkan perubahan yang tiba-tiba dan tidak tepat, dan mengabaikan informasi yang hilang atau tidak tepat [[6](https://www.sciencedirect.com/science/article/abs/pii/B9780080510552500110?via%3Dihub)].

- K-Nearest Neighbor dipilih karena kesederhanaannya jika dibandingkan dengan algoritma lainnya. Berbeda dengan algoritma lain, KNN menggunakan "kesamaan fitur" untuk memprediksi nilai setiap data baru. Dengan kata lain, nilai setiap data baru diberikan berdasarkan seberapa mirip titik tersebut dalam set pelatihan. Kelemahan algoritma ini adalah algoritma ini tidak cocok diimplementasikan pada dataset berukuran besar karena komputasi kompleks dan keterbatasan memori yang dapat meningkatkan waktu komputasi, serta nilai k yang bias [[7](https://www.researchgate.net/publication/324746693_Optimasi_Teknik_Klasifikasi_Modified_K-Nearest_Neighbor_Menggunakan_Algoritma_Genetika)]

- Random Forest dipilih karena merupakan model prediksi yang termasuk dalam model ensemble yaitu model yang merupakan gabungan beberapa model dan bekerja bersama-sama. Hal ini membuat tingkat keberhasilan model menjadi lebih tinggi. Namun, algoritma ini memiliki kelemahan yaitu jumlah pohon dalam model memengaruhi kinerja Random Forest, dimana jumlah pohon yang lebih besar dapat menyebabkan waktu eksekusi lebih lama [[8](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5796274/)].

Dalam membangun keempat model tersebut juga dilakukan penambahan hyperparameter tuning. Pada algoritma SVR, parameter yang dilakukan tuning adalah 'C', 'gamma', dan 'kernel'. Untuk algoritma Decision Trees, dilakukan tuning pada 'max_depth', 'min_samples_leaf', dan 'min_samples_split'. Pada algoritma K-Nearest Neighbor juga dilakukan tuning parameter untuk mencari nilai 'n_neighbors' terbaik, dan untuk algoritma Random Forest juga dilakukan tuning parameter pada 'n_estimators', 'max_depth', 'min_samples_leaf', dan 'min_samples_split'.

Proses tuning ini menggunakan GridSearchCV yang merupakan bagian dari modul scikit-learn untuk mencari parameter terbaik dalam rangka peningkatan performa model dengan cara mencoba seluruh kombinasi hyperparameter yang diberikan.

Berikut adalah tuning parameter yang dilakukan untuk setiap algoritma:

- Support Vector Regression

```python
param_grid_svr = {'C':  [0.1,  1,  10,  100],  'gamma':  [1,  0.1,  0.01,  0.001],  'kernel':  ['linear',  'rbf']}
```

- Decision Trees

```python
param_grid_dt = {'max_depth':  [None,  10,  20,  30,  40,  50],  'min_samples_leaf':  [1,  2,  4],  'min_samples_split':  [2,  5,  10]}
```

- K-Nearest Neighbor

```python
param_grid_knn = {'n_neighbors':  range(1,  21)}
```
- Random Forest

```python
param_grid_rf = {'n_estimators':  [10,  50,  100,  200], 'max_depth':  [None,  10,  20,  30,  40,  50], 'min_samples_leaf':  [1,  2,  4], 'min_samples_split':  [2,  5,  10]}
```

Untuk hasil dari tuning parameter tersebut yang menghasilkan grid.best_params dapat dilihat sebagai berikut:

- Support Vector Regression
> Best parameters for SVR: {'C': 100, 'gamma': 1, 'kernel': 'linear'}

- Decision Trees
> Best parameters for Decision Trees: {'max_depth': 10, 'min_samples_leaf': 4, 'min_samples_split': 10}

- K-Nearest Neighbor
> Best n_neighbors: {'n_neighbors': 15}

- Random Forest
> Best parameters: {'max_depth': 10, 'min_samples_leaf': 1, 'min_samples_split': 10, 'n_estimators': 200}

Parameter dengan nilai tersebut kemudian akan dimasukkan sebagai nilai parameter dari setiap model yang dibuat.

## Evaluation

Teknik evaluasi model yang dilakukan pada proyek ini menggunakan metrik Mean Squared Error,  dimana ini adalah metrik evaluasi yang umum digunakan dalam mengukur seberapa akurat sebuah model regresi memprediksi nilai numerik. MSE menghitung selisih antara nilai prediksi model dan nilai sebenarnya dari data, kemudian mengkuadratkan selisih yang diperoleh agar tidak ada selisih yang memiliki nilai negatif. Lalu, selisih kuadrat kemudian dijumlahkan dan diambil sebagai rata-rata dari semua sampel data.

MSE dapat didefinisikan dalam persamaan berikut:

![Image 13](https://miro.medium.com/v2/resize:fit:828/format:webp/1*BtVajQNj29LkVySEWR_4ww.png)

Berikut merupakan perbandingan hasil nilai error train dan test dari keempat model yang digunakan:

|     |train|test|
|---|---|---|
|SVR|86051881127.030975|87820728254.917694|
|Decision Trees|16267242476.414715|25450620244.534927|
|KNN|18167566509.839661|23294296282.151714|
|Random Forest|14611530632.471609|22247655202.370575|

Berdasarkan hasil evaluasi dapat dilihat bahwa model dengan algoritma Random Forest memiliki tingkat error yang lebih rendah dibandingkan algoritma lainnya dalam proyek ini.

Perbandingan tersebut juga dapat dilihat pada gambar dibawah ini

![Image 14](https://github.com/cyncindy/Predictive-Analytics-Price-Prediction/blob/main/images/Evaluation.png?raw=true)

Dalam rangka menguji performa model yang dibuat, maka dilakukan prediksi menggunakan beberapa harga dari data test yang hasilnya dapat dilihat sebagai berikut:

|     |y_true|prediksi_SVR|prediksi_Decision Trees|prediksi_KNN|prediksi_Random Forest|
|---|---|---|---|---|---|
|4201|6923590.0|12145526.6|12714969.6|10957071.5|10756553.6|
|18108|5838315.0|9542192.9|5853908.2|5963878.6|6175396.9|
|19304|7571718.0|9894654.1|7904677.2|7725579.8|7783419.0|
|5832|12000000.0|10439436.9|10646798.2|10866197.6|10904275.3|
|4795|18990000.0|10758041.8|16716315.8|18132000.0|16372857.7|

Dengan demikian dapat disimpulkan bahwa model yang telah dikembangkan dapat memprediksi harga rumah dengan baik dengan menggunakan algoritma Random Forest.

## Referensi

[1] A. A. Manaf, G. I. Zheng, "Faktor-faktor penentu harga rumah dari perspektif pemaju perumahan", Malaysian Journal of Society and Space, vol. 15, no. 4, pp. 246-260, November 2019, doi: 10.17576/geo-2019-1504-18

[2] V. Amaresh, R. R. Singh, R. Kamal and A. Kulkarni, "Linear Regression Models based Housing Price Forecasting," 2022 International Conference on Industry 4.0 Technology (I4Tech), Pune, India, 2022, pp. 1-5, doi: 10.1109/I4Tech55392.2022.9952397

[3] R. Isnaeni, Sudarmin, R. Zulkifli, "Analisis Support Vector Regression (SVR) Dengan Kernel Radial Basis Function (RBF) Untuk Memprediksi Laju Inflasi di Indonesia", VARIANSI:Journal of Statistics and Its Application on Teaching and Research, vol. 4, no. 1, pp. 30-38, 2022, doi: 10.35580/variansiunm13

[4] H. Muhamad, I. Cholissodin, dan B. D. Setiawan, "Optimasi Support Vector Regression (SVR) Menggunakan Algoritma Improved-Particle Swarm Optimization (IPSO) untuk Peramalan Curah Hujan", J-PTIIK, vol. 1, no. 11, hlm. 1142–1151, Jul 2017.

[5] T. Thomas, A. P. Vijayaraghavan, S. Emmanuel, "Applications of Decision Trees. In: Machine Learning Approaches in Cyber Security Analytics", Springer, Singapore, 2020, doi: 10.1007/978-981-15-1706-8_9

[6] J. Quinlan, "Probabilistic decision trees. Machine Learning", 1990. pp. 140-152. doi: 10.1016/B978-0-08-051055-2.50011-0

[7] S. Mutrofin, M. Masrur, "Optimasi Teknik Klasifikasi Modified K-Nearest Neighbor Menggunakan Algoritma Genetika", 2014, doi: 10.13140/RG.2.2.22330.08648

[8] P. T. Noi, M. Kappas, "Comparison of Random Forest, k-Nearest Neighbor, and Support Vector Machine Classifiers for Land Cover Classification Using Sentinel-2 Imagery", Sensors, vol. 18, no. 1, 2018, doi: 10.3390/s18010018
