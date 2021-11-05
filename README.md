# Laporan Proyek Machine Learning - Alifia Feiling A.S

## Domain Proyek

Domain proyek yang dipilih dalam proyek _machine learning_ ini adalah mengenai **Keuangan** dengan judul proyek "Prediksi Data Biaya Asuransi Kesehatan yang Dikeluarkan Pasien".
-   Latar Belakang
<p align="center">
  <img width="460" height="300" src="https://wwwassets.rand.org/content/rand/blog/2012/03/the-real-cost-of-healthcare/jcr:content/par/blogpost.aspectcrop.868x455.cm.jpg/1548810183805.jpg" alt="https://www.rand.org/blog/2012/03/the-real-cost-of-healthcare.html">
</p>
Biaya  asuransi kesehatan merupakan jenis perlindungan asuransi yang menanggung biaya medis, bedah, obat-obatan, dan sejenisnya untuk tertanggung atau pemegang polis. Biaya asuransi kesehatan yang dikeluarkan tergantung dari hasil pemeriksaan data pemegang polis. Biaya yang dikeluarkan oleh pasien dapat diganti oleh asuransi seluruhnya atau sebagian tergantung dari asuransi yang digunakan.

Untuk itu penulis mengambil judul proyek **Prediksi Data Biaya Asuransi Kesehatan yang Dikeluarkan Pasien** yang digunakan untuk memprediksi biaya asuransi yang akan dikeluarkan Pasien.Proyek ini dibuat menggunakan model _machine learning_ untuk mengklasifikasikan data biaya asuransi yang dikeluarkan pasien. Dengan adanya model _machine learning_ diharapkan memudahkan pasien dalam memprediksi biaya asuransi kesehatan yang akan dikeluarkan.

## Business Understanding

### Problem Statements

Berdasarkan latar belakang diatas, berikut ini merupakan rincian masalah yang dapat diselesaikan pada proyek ini :

-   Bagaimana cara melakukan pra-pemrosesan data biaya asuransi kesehatan agar dapat digunakan untuk membuat model yang baik?
-   Bagaimana cara membuat model _machine learning_ untuk mengklasifikasi data biaya asuransi kesehatan yang akan dikeluarkan oleh pasien?

### Goals

Berikut adalah tujuan dari dibuatnya proyek ini :

-   Melakukan pra-pemrosesan data biaya asuransi kesehatan yang baik agar dapat digunakan dalam membuat model.
-   Membuat model _machine learning_ untuk mengklasifikasikan data biaya asuransi kesehatan yang memiliki tingkat akurasi > 75%.

### Solution statements

Solusi yang dapat dilakukan untuk memenuhi tujuan dari proyek ini diantaranya :

-   Untuk pra-pemrosesan data dapat dilakukan beberapa teknik, diantaranya :

    -   Menkonversi kolom (sex, smoker, region) dari bentuk string ke bentuk numerik
    -   Melakukan **pembagian dataset** menjadi dua bagian dengan rasio 80% untuk data latih dan 20% untuk data uji

    Poin pra-pemrosesan data akan dibahas lebih lanjut pada bagian `Data Preparation`.

-   Untuk pembuatan model dipilih penggunaan model dengan algoritma **Linear Regression, Support Vector Regression, Random Forest Regressor dan Gradient Boosting Regressor** untuk _Klasifikasi_ . Algoritma tersebut dipilih karena cocok untuk penyelesaian kasus klasifikasi.

Cara kerja algoritma **Linear Regression, Support Vector Regression, Random Forest Regressor, dan Gradient Boosting Regressor** akan dijelaskan dibawah ini.

**1. Linear Regression**

Linear Regression digunakan untuk memodelkan hubungan antara suatu (satu atau lebih) variabel dependen dengan satu (regresi linear sederhana) atau lebih variabel independen (regresi linier banyak). Salah satu aplikasi dari Linear Regression adalah untuk melakukan prediksi berdasarkan data-data yang telah dimiliki sebelumnya.
  
**2. Support Vector Regression**
 
Support Vector Regression (SVR) merupakan metode klasik yang memanfaatkan teori matematika dan statistik untuk regresi dengan model Support Vector Machine (SVM). Jadi SVM ternyata bukan hanya untuk klasifikasi melainkan juga untuk regresi dan deteksi outliers.

**3. Random Forest Regressor**

Random Forest Regressor adalah suatu algoritma yang digunakan pada klasifikasi data dalam jumlah yang besar. Klasifikasi Random Forest Regressor dilakukan melalui penggabungan pohon (tree) dengan melakukan training pada sampel data yang dimiliki.

**4. Gradient Boosting Regressor**

 Gradient Boosting Regressor adalah algoritma machine learning yang menggunakan ensamble dari decision tree untuk memprediksi nilai. Sturktur data dari gradient boosting adalah decision tree. Decision tree adalah model dengan cabang pilihan (decision branch), nilai ditentukan dengan mengikuti alur cabang pilihan.

## Data Understanding

![kesehatan](https://user-images.githubusercontent.com/83399671/140502453-7caf1069-0f7a-4589-bdcd-9c7ebc0c4f98.png)


Informasi dataset dapat dilihat pada tabel dibawah ini :
| Jenis                   | Keterangan                                                                                                         |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Sumber                  | [Medical Cost Personal Datasets](https://www.kaggle.com/mirichoi0218/insurance) |
| Lisensi                 | CC0: Public Domain                                                                                                 |
| Kategori                | Keuangan                                                                                                           |
| Jenis dan Ukuran Berkas | CSV (55.63 kb)  

   Pada berkas yang diunduh yakni `insurance.csv` berisi informasi untuk 1338 data kepribadian pelanggan yang berbeda. Terdapat 2 buah data numerik (tipe data float64), 2 buah data kategori (tipe data int64), dan 3 buah data objek (object) dan tidak memiliki data kosong. Untuk penjelasan mengenai variabel-variabel pada data _asuransi_ dapat dilihat pada poin-poin berikut :

1. `age` : data umur

2. `sex`: data antara pria atau wanita

3. `bmi` : data Indeks massa tubuh (Body Mass Index)

4. `children`: data anak yang terlindungi oleh asuransi

5. `smoker` : data antara perokok atau tidak perokok

6. `region` : data daerah di US

7. `charges`: data biaya pengobatan individu yang ditagih oleh asuransi kesehatan

Kemudian terdapat juga visualisasi data seperti pada gambar dibawah ini :


`Korelasi data antar fitur`

![korelasi](https://user-images.githubusercontent.com/83399671/140504400-247e78ed-d0cf-4bed-a339-42a67b185bcf.png)


`Tidak ada data kosong`

![data kosong](https://user-images.githubusercontent.com/83399671/140504452-768e6a88-5f20-4567-b33a-d76d8f3d4773.png)


`Kolom charges berelasi dengan kolom bmi dan age`

![bmi dengan umur](https://user-images.githubusercontent.com/83399671/140504551-4b463c30-23fc-4050-9d42-4000af53b6c6.png)


`Kolom charges yang berelasi dengan kolom sex = perempuan`

![kolom sex perempuan](https://user-images.githubusercontent.com/83399671/140504645-e5a0683e-cfdb-4dba-a6b0-eaa3d8a17517.png)


`Kolom charges yang berelasi dengan kolom sex = pria`

![kolom sex pria](https://user-images.githubusercontent.com/83399671/140504698-47373b68-305e-4390-8153-95d09c97afd2.png)


`Kolom charges yang berelasi dengan kolom smoker = iya`

![kolom perokok](https://user-images.githubusercontent.com/83399671/140504755-8ba2806a-1760-4594-a13a-6fe816323f45.png)


`Kolom charges yang berelasi dengan kolom smoker = tidak`

![kolom tidak perokok](https://user-images.githubusercontent.com/83399671/140504812-528c8418-45e9-40d7-b709-9d6a6947892c.png)



## Data Preparation

Seperti yang sudah disebutkan sebelumnya pada bagian _Solution statements_, berikut adalah tahapan-tahapan dalam melakukan pra-pemrosesan data :

 -   Mengkonversi kolom (sex, smoker, region) dari bentuk string ke bentuk numerik

 ![konversi fitur](https://user-images.githubusercontent.com/83399671/140505099-08790e81-05c0-4302-a89b-460ecfd4cc07.png)
 
 Terlihat pada gambar diatas hasil dari konversi fitur string pada kolom (sex, smoker, region) ke bentuk numerik.

 -    Melakukan **pembagian dataset** menjadi dua bagian dengan rasio 80% untuk data latih dan 20% untuk data uji

 Pengujian performa model pada data sebenarnya, maka perlu dilakukan pembagian dataset kedalam dua atau tiga bagian. Pada proyek ini dilakukan dua bagian saja yakni pada data latih dan data uji dengan rasio 80:20. Data latih dilakukan sepenuhnya untuk melatih model, sedangkan data uji merupakan data yang belum pernah dilihat oleh model dan diharapkan model dapat memiliki performa yang sama baiknya pada data uji seperti pada data latih.Pembagian dataset dilakukan dengan modul train_test_split dari scikit-learn

## Data Modeling

Setelah melakukan pra-pemrosesan data yang baik pada tahap modeling akan dilakukan menggunakan 4 Algoritma dalam _machine learning_ yaitu : Linear Regression, Support Vector Regression, Random Forest Regressor, dan Gradient Boosting Regressor.

![perbandingan model](https://user-images.githubusercontent.com/83399671/140505643-fc5f827b-0b9d-4227-8104-6004c0c83de2.png)

Terlihat pada tabel diatas menampilkan perbandingan hasil prediksi masing - masing algoritma dengan data aktualnya yang terdiri dari : Linear Regression (Lr), Support Vector Regression (svm), Random Forest Regressor (rf), dan Gradient Boosting Regressor (gr).

Selain pada tabel diatas, hasil visualisasi antar model dapat dilihat pada gambar dibawah ini :

![algoritma](https://user-images.githubusercontent.com/83399671/140496130-6fb0eeaa-8bab-4432-9d8c-169f3480c8f1.png)

_Keterangan Gambar_:
1. Garis Biru menunjukkan data Aktual
2. Garis Oranye menunjukkan hasil fitting Algoritma


**1. Linear Regression**

Linear Regression digunakan untuk memodelkan hubungan antara suatu (satu atau lebih) variabel dependen dengan satu (regresi linear sederhana) atau lebih variabel independen (regresi linier banyak). Salah satu aplikasi dari Linear Regression adalah untuk melakukan prediksi berdasarkan data-data yang telah dimiliki sebelumnya. Model Linear Regression pada gambar diatas belum mendekati dengan data aktualnya.
  
  
**2. Support Vector Regression**
 
Support Vector Regression (SVR) merupakan metode klasik yang memanfaatkan teori matematika dan statistik untuk regresi dengan model Support Vector Machine (SVM). Jadi SVM ternyata bukan hanya untuk klasifikasi melainkan juga untuk regresi dan deteksi outliers. Model Support Vector Regression pada gambar diatas masih belum bisa mendekati dengan data aktualnya.
  
**3. Random Forest Regressor**

Random Forest Regressor adalah suatu algoritma yang digunakan pada klasifikasi data dalam jumlah yang besar. Klasifikasi Random Forest Regressor dilakukan melalui penggabungan pohon (tree) dengan melakukan training pada sampel data yang dimiliki. Model Random Forest Regressor pada gambar diatas hampir mendekati dengan data aktualnya.

**4. Gradient Boosting Regressor**

 Gradient Boosting Regressor adalah algoritma machine learning yang menggunakan ensamble dari decision tree untuk memprediksi nilai. Model Gradient Boosting Regressor pada gambar diatas mendekati dengan data aktualnya.
 
Melihat gambar visualisasi diatas dapat terlihat Gradient Boosting Regressor adalah model terbaik untuk dataset ini.

##  Data Evaluation

Dalam melakukan evaluasi menggunakan _metrics.r2_score_ untuk menghitung hasil score regresi dan _mean absolute error_ adalah rata-rata selisih mutlak nilai sebenarnya (aktual) dengan nilai prediksi (peramalan). Dibawah ini terlampir hasil dari _metrics.r2_score_ dan _mean absolute error_ :

`metrics.r2_score`

![r2 score](https://user-images.githubusercontent.com/83399671/140511030-0555fba2-fe89-438f-b0aa-53e0fede00c6.png)

`mean absolute error`

![mae](https://user-images.githubusercontent.com/83399671/140511319-01c50f3c-639d-476f-a4e3-f7a01bbb3f2e.png)


## Prediksi Biaya

Prediksi biaya dilakukan untuk memeriksa prediksi biaya asuransi yang dikeluarkan oleh pasien. Prediksi biaya yang dipakai menggunakan algoritma Gradient Boosting Regressor karena melihat dari hasil yang menunjukkan kinerja terbaik. Dibawah ini adalah hasil dari prediksi biaya :

![prediksi biaya](https://user-images.githubusercontent.com/83399671/140511674-1b907bf9-dfbb-4f03-b0ed-c76fb2d6b982.png)


## Kesimpulan 

Model machine learning yang terbaik adalah _Gradient Boosting Regressor_ karena dari hasil visualisasi performa, model ini mendekati dengan data aktualnya.

## _Referensi_

1.  Han, Jiawei.2012. Data Mining Concepts and Techniques Third Edition. USA : Elsevier
2.  McNulty, Keith·2021. Handbook of Regression Modeling in People Analytics With Examples in R and Python
3.  Hosmer, D.W dan S.Lemeshow. 2000. Applied Logistic Regression. 2nd Edition. New York: John Willey and Sons

**---Ini adalah bagian akhir laporan---**
