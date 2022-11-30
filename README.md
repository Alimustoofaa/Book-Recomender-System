
# Proyek Akhir Recomender System
#### Disusun oleh : Ali Mustofa


## **Project Overview**

Sistem rekomendasi buku merupakan sistem yang merekomendasikan buku kepada pembaca atau pembeli. Sistem rekomendasi yang saya buat ini didasarkan dengan peferensi kesukaan pengguna dimasa lalu, serta rating dari buku tersebut. Sistem rekomendasi telah menjadi lazim dalam beberapa tahun terakhir, karena mereka menangani masalah informasi dengan menyarankan penggunaan produk yang paling relevan dari sejumlah data besar. Sekarang sistem rekomendasi sangat penting dibeberapa industri karena dapat menghasilkan pendapatan yang sangat besar jika efisien. Dalam makalah ini, diusulkan sistem rekomendasi buku berbasis model hibrida yang memanfaatkan pengelompokan K-means yang ditingkatkan ditambah dengan algoritma genetika (GAs) untuk mempartisi ruang pengguna yang ditransformasikan. Ini menggunakan teknik reduksi data analisis komponen utama (PCA) untuk memadat ruang populasi buku yang juga dapat mengurangi kompleksitas komputasi dalam rekomendasi buku cerdas. Hasil eksperimen pada dataset Arashnic menunjukkan bahwa pendekatan yang diusulkan dapat memberikan kinerja tinggi dalam hal akurasi, dan menghasilkan rekomendasi film yang lebih andal dan personal jika dibandingkan dengan metode yang ada.
<br>

<div><img src="https://elearningindustry.com/wp-content/uploads/2016/05/top-10-books-every-college-student-read-e1464023124869.jpeg" width="1000"/></div>
<br>

## Business Understanding

### Problem Statement

1. Bagaimana cara merecomendasikan buku yang disukai oleh pembaca lain, direcomendasikan ke pembaca lain.

### Goals

1. Dapat membuat sistem rekomendasi yang akurat berdasarkan ratings dan aktivitas pengguna pada masa lalu.

### Solution Statement
Solusi yang saya buat yaitu dengan menggunakan 2 algoritma Machine Learning sistem rekomendasi,yaitu :
1. *Content Based Filtering* adalah algoritma yang merekomendasikan item serupa dengan apa yang disukai pengguna, berdasarkan tindakan mereka sebelumnya atau umpan balik eksplisit.
2. *Collaborative Filtering*. adalah algoritma yang bergantung pada pendapat komunitas pengguna. Dia tidak memerlukan atribut untuk setiap itemnya.

Algoritma *Content Based Filtering* digunakan untuk merekemondesikan movie berdasarkan aktivitas pengguna pada masa lalu, sedangkan algoritma *Collabarative Filltering* digunakan untuk merekomendasikan movie berdasarkan ratings yang paling tinggi.

## Data Understanding & Removing Outlier

Data atau dataset yang digunakan pada proyek machine learning ini adalah data **Book Recommendation Dataset** yang didapat dari situs kaggle. Link dataset dapat dilihat dari tautan berikut [book-recommendation-dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset?select=Books.csv)
Variabel-variabel pada book-recommendation-datasets adalah sebagai berikut :
* books : data buku
* ratings: data penilaian yang diberikan pengguna terhadap buku
* user : data pengguna yang membaca buku

### Data Preparation

-   Mengatasi missing value : Menyeleksi data apakah data tersebut ada yang kosong atau tidak, jika ada data kosong maka data akan dihapus
-  Memfilter data : mengambil data book rating yang memiliki jumlah rating besar dari 200
-   Menggabungkan variabel : untuk menggabungkan beberapa variabel berdasarkan ISBN yang sifatnya unik (berbeda dari yang lain).
-   Konversi data menjadi iist : untuk mengubah data menjadi list
-   Membuat dictionary : Untuk membuat dictionary dari data yang ada.
-   Menggunakan TfidfVectorizer : untuk melakukan pembobotan.
-   melakukan preprocessing : untuk menghilangkan permasalahan-permasalahan yang dapat mengganggu hasil daripada proses data
-   mapping data : untuk memetakan data

###  Modeling and Result

 Proses modeling yang saya lakukan pada data ini adalah dengan membuat algoritma machine learning, yaitu content based filtering dan collabrative filtering. untuk algoritma content based filtering saya buat dengan apa yang disukai pengguna pada masa lalu, sedangkan untuk content based filtering, saya buat dengan memanfaatkan tingkat rating dari buku tersebut.
 
### Evaluation
Berikut hasil evaluasi dari kedua algoritma:
1. Content Based Filtering
  <div><img src="https://user-images.githubusercontent.com/56061857/204862913-82c1054c-0e16-4e17-91db-bfea9d5b9b28.png" width="450"/></div>

Dari Hasil rekomendasi diatas, hasil rekomendasi buku 1st to Die: A Novel dan jika salah satu hasil tersbut dimasukkan ke rekomendasi dari 5 hasil rekomendasi terdapat 3 rekomendasi sama. Artinya, precision sistem kita sebesar 3/5 atau 60%Multivariate Analysis menunjukkan hubungan antara dua atau lebih fitur dalam data.
Teknik Evaluasi di atas adalah dengan menggunakan precission, rumus dari teknik ini adalah :
  <div><img src="https://user-images.githubusercontent.com/56061857/204862975-590c8d50-0675-4057-b084-937faf0ef4a9.png" width="450"/></div>

2.  Collaborative Content Filtering.
Evaluasi metrik yang digunakan untuk mengukur kinerja model adalah metrik RMSE (Root Mean Squared Error).
	-   RMSE adalah metode pengukuran dengan mengukur perbedaan nilai dari prediksi sebuah model sebagai estimasi atas nilai yang diobservasi. Root Mean Square Error adalah hasil dari akar kuadrat Mean Square Error. Keakuratan metode estimasi kesalahan pengukuran ditandai dengan adanya nilai RMSE yang kecil. Metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih kecil dikatakan lebih akurat daripada metode estimasi yang mempunyai Root Mean Square Error (RMSE) lebih besar
	-   Kelebihan dan kekurang matriks ini adalah :
	    **kelebihan**  : menghukum kesalahan besar lebih sehingga bisa lebih tepat dalam beberapa kasus.  
	    **Kekurangan**  : memberikan bobot yang relatif tinggi untuk kesalahan besar. Ini berarti RMSE harus lebih berguna ketika kesalahan besar sangat tidak diinginkan
	    
	-   formula dari matriks RMSE adalah sebagai berikut
  <div><img src="https://user-images.githubusercontent.com/56061857/204863144-b56091a3-1cd7-4330-be75-b8aae4b86733.png" width="450"/></div>
	keterangan :  
At : Nilai Aktual.  
ft = Nilai hasil peramalan.  
N = banyaknya dataset

cara menerapkan metrik tersebut adalah dengan menambahkan **_'metrics=[tf.keras.metrics.RootMeanSquaredError()]'_** pada model.compile sehingga menjadi seperti berikut :
  <div><img src="https://user-images.githubusercontent.com/56061857/204863435-c136da84-3a4f-4cc0-b27e-df8d53c97837.png" width="450"/></div>

hasil dari model evaluasi visualisasi matriks adalah sebagai berikut :

dari visualisasi proses training model di atas cukup smooth dan model konvergen pada epochs sekitar 10. Dari proses ini, saya memperoleh nilai error akhir sebesar sekitar 0.3235 dan error pada data validasi sebesar 0.3496.

### Evaluation
Dapat dilihat dari kedua model Algoritma yang dikembangkan, dapat disimpulkan dari hasil perbandingan serta visualisasi perbandingan rekomendasi dua Algoritma yaitu Content Based Filtering, Collaborative Filtering . dapat disimpulkan bahwa kedua model tersebut memiliki kelebihan dan kekurangan masing-masing. 
