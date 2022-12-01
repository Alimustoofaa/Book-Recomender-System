


# Proyek Akhir Recomender System
#### Disusun oleh : Ali Mustofa


## **Project Overview**

Sistem rekomendasi buku merupakan sistem yang merekomendasikan buku kepada pembaca atau pembeli. Sistem rekomendasi ini didasarkan dengan peferensi kesukaan pengguna dimasa lalu, serta rating dari buku tersebut. Sistem rekomendasi telah menjadi lazim dalam beberapa tahun terakhir, karena mereka menangani masalah informasi dengan menyarankan penggunaan produk yang paling relevan dari sejumlah data besar. Sekarang sistem rekomendasi sangat penting dibeberapa industri karena dapat menghasilkan pendapatan yang sangat besar jika efisien. Dalam makalah ini, diusulkan sistem rekomendasi buku berbasis model hibrida yang memanfaatkan pengelompokan K-means yang ditingkatkan ditambah dengan algoritma genetika (GAs) untuk mempartisi ruang pengguna yang ditransformasikan. Ini menggunakan teknik reduksi data analisis komponen utama (PCA) untuk memadat ruang populasi buku yang juga dapat mengurangi kompleksitas komputasi dalam rekomendasi buku cerdas. Hasil eksperimen pada dataset Arashnic menunjukkan bahwa pendekatan yang diusulkan dapat memberikan kinerja tinggi dalam hal akurasi, dan menghasilkan rekomendasi film yang lebih andal dan personal jika dibandingkan dengan metode yang ada.
<br>

<div><img src="https://elearningindustry.com/wp-content/uploads/2016/05/top-10-books-every-college-student-read-e1464023124869.jpeg" width="1000"/></div>
<br>

## Business Understanding

### Problem Statement

1. Bagaimana cara merekomendasikan buku yang disukai oleh pembaca lain, merekomendasikan ke pembaca lain.

### Goals

1. Dapat membuat sistem rekomendasi yang akurat berdasarkan ratings dan aktivitas pengguna pada masa lalu.

### Solution Statement
Solusi ini buat yaitu dengan menggunakan 2 algoritma Machine Learning sistem rekomendasi,yaitu :
1. *Content Based Filtering* adalah algoritma yang merekomendasikan item serupa dengan apa yang disukai pengguna, berdasarkan tindakan mereka sebelumnya atau umpan balik eksplisit.
2. *Collaborative Filtering*. adalah algoritma yang bergantung pada pendapat komunitas pengguna. Dia tidak memerlukan atribut untuk setiap itemnya.

Algoritma *Content Based Filtering* digunakan untuk merekemondesikan movie berdasarkan aktivitas pengguna pada masa lalu, sedangkan algoritma *Collabarative Filltering* digunakan untuk merekomendasikan movie berdasarkan ratings yang paling tinggi.

## Data Understanding 

Data atau dataset yang digunakan pada proyek machine learning ini adalah data **Book Recommendation Dataset** yang didapat dari situs kaggle. Link dataset dapat dilihat dari tautan berikut [book-recommendation-dataset](https://www.kaggle.com/datasets/arashnic/book-recommendation-dataset?select=Books.csv)
Variabel-variabel pada book-recommendation-datasets adalah sebagai berikut :
* books : data buku
* ratings: data penilaian yang diberikan pengguna terhadap buku
* user : data pengguna yang membaca buku

### Data Preparation

#### Mengatasi missing value 
 Menyeleksi data apakah data tersebut ada yang kosong atau tidak, jika ada data kosong maka data akan dihapus. data books dan user memiliki row kosong, maka row tersebut akan dihapus. Berikut hasilnya:

| users    |        |
|----------|--------|
| User-ID  | 0      |
| Location | 0      |
| Age      | 110762 |

Dari table diatas colum Age ditable users memiliki missing value yang sangat banyak, sehingga column Age dihapus.

| users               |   |
|---------------------|---|
| ISBN                | 0 |
| Book-Title          | 0 |
| Book-Author         | 1 |
| Year-Of-Publication | 0 |
| Publisher           | 2 |
| Image-URL-S         | 0 |
| Image-URL-M         | 0 |
| Image-URL-L         | 3 |

Dari table diatas ada sedikit missing value di column Book-Author, Publisher, Image-URL-L. Sehingga row tersebut dihapus.

#### Memfilter data 
Mengambil data book rating yang memiliki jumlah rating besar dari 200. Hasil tersebut yang semula data nya berjumlah 1.031.129 row menjadi 474.003.
#### Menggabungkan variabel 
menggabungkan data buku dan rating berdasarkan data column yang sifatnya unik. Dari data yang digunakan, colum tersebut adalah ISBN.
####  Konversi data menjadi list
Mengkonversi data di kolom User-ID dan ISBN menjadi list. Dari hasil tersebut digunakan untuk encode kedictonary.
#### Membuat dictionary 
Dari hasil mengkonversi ke list selanjutkan list User-ID dan ISBN  diencode ke dictionary. Terdapat 2 encode dimasing-masing data, yaitu dari dictionary berisi key index dan value nilai dari data tersebut. kedua berisi ket nilai data dan value index dari data tersebut.

#### Melakukan preprocessing 
Yntuk menghilangkan permasalahan-permasalahan yang dapat mengganggu hasil daripada proses data. Mengacak dataset dengan menggunakan fungsi df.sampe dengan param frac=1 dan random state=42

###  Modeling and Result

 Proses modeling yang  dilakukan pada data ini adalah dengan membuat algoritma machine learning, yaitu content based filtering dan collabrative filtering. untuk algoritma content based filtering  dibuat dengan apa yang disukai pengguna pada masa lalu, sedangkan untuk content based filtering,  dibuat dengan memanfaatkan tingkat rating dari buku tersebut. Berikut hasil dari 2 algoritma tersebut:
 

 1. Content Based Filtering
 algoritma tersebut  merekomendasikan buku serupa dengan apa yang disukai pengguna, berdasarkan tindakan mereka sebelumnya atau umpan balik eksplisit.
<div><img src="https://user-images.githubusercontent.com/56061857/204862913-82c1054c-0e16-4e17-91db-bfea9d5b9b28.png" width="450"/></div>
Dari hasil tersbut memiliki hasil yang sama dengan melakukan uji menggunakan judul buku yang berbeda yaitu Vilotes Are Blue dan Pop Goes the Weasel.

 2. Collaborative Content Filtering.
 algoritma tersebut bergantung pada pendapat komunitas pengguna. Dia tidak memerlukan atribut untuk setiap itemnya.
 <div><img src="https://user-images.githubusercontent.com/56061857/204974665-4b40f0e9-d919-4673-9903-287f1ec65a98.png" width="450"/></div>
 Dari hasil tersebut memiliki 10 rekomendasi terbaik berdasarkan yang dibaca user


 
### Evaluation
Berikut hasil evaluasi dari kedua algoritma:
1. Content Based Filtering
Dari Hasil rekomendasi Content Based Filtering, hasil rekomendasi buku 1st to Die: A Novel dan jika salah satu hasil tersbut dimasukkan ke rekomendasi dari 5 hasil rekomendasi terdapat 3 rekomendasi sama. Artinya, precision sistem kita sebesar 3/5 atau 60%Multivariate Analysis menunjukkan hubungan antara dua atau lebih fitur dalam data.
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

dari visualisasi proses training model di atas cukup smooth dan model konvergen pada epochs sekitar 10. Dari proses ini memperoleh nilai error akhir sebesar sekitar 0.3235 dan error pada data validasi sebesar 0.3496.

### Kesimpulan
Dapat dilihat dari kedua model Algoritma yang dikembangkan, dapat disimpulkan dari hasil perbandingan serta visualisasi perbandingan rekomendasi dua Algoritma yaitu Content Based Filtering, Collaborative Filtering . dapat disimpulkan bahwa kedua model tersebut memiliki kelebihan dan kekurangan masing-masing. 
