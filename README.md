


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

 Proses modeling yang  dilakukan pada data ini adalah dengan membuat algoritma machine learning, yaitu content based filtering dan collabrative filtering. untuk  content based filtering  menggunakan algoritma *Cosine Similarity* algoritma tersebut mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama.  Sedangkan collabrative filtering  menggunakan *User-Based* untuk mendapatkan rekomendasi disini menggunakan penilaian dari pengguna untuk mendapatkan rekomendasi buku-buku . Berikut hasil dari 2 algoritma tersebut:
 

 1. Content Based Filtering
 Menggunakan algoritm *Cosine Similarity* algoritma tersebut mengukur kesamaan antara dua vektor dan menentukan apakah kedua vektor tersebut menunjuk ke arah yang sama. Ia menghitung sudut cosinus antara dua vektor. Semakin kecil sudut cosinus, semakin besar nilai cosine similarity.  Dari algoritma tersebut bisa bisa diterapkan dengan mengukur kesamaan dari judul buku. 

|recommend ('1st to Die: A Novel')     |
|-----------------------------------------|
| Along Came a Spider (Alex Cross Novels) |
| Roses Are Red (Alex Cross Novels)       |
| Pop Goes the Weasel                     |
| Violets Are Blue                        |
| Lightning                               |


| recommend ('Roses Are Red (Alex Cross Novels')|
|---------------------------------------------------|
| Kiss the Girls                                    |
| Violets Are Blue                                  |
| 1st to Die: A Novel                               |
| The Murder Book                                   |
| Pop Goes the Weasel                               |

Dari hasil tersbut memiliki hasil yang sama dengan melakukan uji menggunakan judul buku yang berbeda yaitu Vilotes Are Blue dan Pop Goes the Weasel.

 - Collaborative Content Filtering.
Dalam  Collaborative Content Filtering disini menggunakan data data user dan rating untuk menghasilkan rekomendasi berdasarkan preferensi pengguna berdasarkan rating yang telah diberikan sebelumnya. Dari data yang ada berikut adalah processnya:
	 - Preparing data: data yang digunakan adalah data rating
	 - Penambahan column:  menambahkan column book yang berisi encode index isbn dan user berisi encode index user untuk dijadikan data training.
	 - Mengacak data: Sebelum training data diacak untuk menghasilkan data train yang baik
	 - Train test dataset: Selanjutnya membagi data train dan test dengan komposisi 70% data train dan 30% data test
	 -  Model : Disini menggunakan model keras dengan menghidung kecocokan antara num_user dan num_isbn dengan teknik embedding.
	 - Compile model: Model ini menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan root mean squared error (RMSE) sebagai metrics evaluation.
	 - Training process: Ditahap training process disini menggunakan model dengan batch_size =. 64 dan epochs =10.
	 -  Testing model: Berikut hasil testing model:

|Top 10 Book Recommendation for user: 78834|
|-----------------------------------------------------------------------------------------------------------------------------------|
| Animal Farm : George Orwell                                                                                                       |
| Captain Underpants and the Attack of the Talking Toilets: Another Epic Novel (Captain Underpants (Paper)) : Dav Pilkey            |
| Harry Potter and the Order of the Phoenix (Book 5) : J. K. Rowling                                                                |
| Angus, Thongs and Full-Frontal Snogging: Confessions of Georgia Nicolson : Louise Rennison                                        |
| The Color Purple : Alice Walker                                                                                                   |
| The Lost Boy: A Foster Child's Search for the Love of a Family : Dave Pelzer                                                      |
| A Light in the Attic : Shel Silverstein                                                                                           |
| Good Work, Amelia Bedelia : Peggy Parish                                                                                          |
| Cooking with Mickey &amp; Friends : More Than 30 Recipes for Kids Easy to Make and Even Easier to Eat! (Disneys) : Patricia Baird |
| After the Plague: Stories : T. Coraghessan Boyle                                                                                  |

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
