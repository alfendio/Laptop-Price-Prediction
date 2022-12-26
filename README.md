# Laporan Proyek Machine Learning - Alfendio Alif Faudisyah

## Domain Proyek
Pada era modern ini kebutuhan teknologi berbasis komputer telah menjadi kebutuhan utama bagi masyarakat. Salah satu perangkat komputer yang banyak digunakan adalah laptop. Kebutuhan akan laptop tersebut memunculkan bisnis jual beli pada laptop. Orang awam banyak yang tidak mengetahui mengenai harga laptop karena tiap laptop memiliki spesifikasi yang berbeda. Oleh karena itu dibuatlah suatu sistem yang dapat memprediksi harga laptop sehingga dapat memudahkan pembeli laptop untuk mengetahui harga laptop.

## Business Understanding
### Problem Statements
- Ketidaktahuan orang awam atau konsumen laptop mengenai harga laptop berdasarkan spesifikasi.

### Goals
- Membuat sistem yang dapat memprediksi harga laptop berdasarkan spesifikasi.

## Data Understanding
Dataset didapatkan dari Kaggle. [Laptop Price](https://www.kaggle.com/datasets/muhammetvarl/laptop-price)

### Variabel-variabel pada Laptop Price dataset adalah sebagai berikut:
- Company : Produsen laptop
- Product : Merk dan model
- TypeName : Tipe, contoh Notebook, Ultrabook, Gaming, dll.
- Inches : Ukuran layar dalam inch
- ScreenResolution : Resolusi layar
- Cpu : CPU laptop
- Ram : RAM laptop
- Memory : Memory hard disk atau SSD
- GPU : GPU laptop
- OpSys : Sistem operasi laptop
- Weight : Berat laptop 
- Price_euros : Harga dalam euro

## Data Preparation
- Melakukan pengumpulan dataset untuk mengukur informasi mengenai variabel-variabel yang ditargetkan.
- Melakukan pembersihan dataset untuk menghapus atau memodifikasi data yang tidak sesuai.
- Melakukan standarisasi dataset untuk menyeragamkan data hingga seluruh data menjadi standar.
- Melakukan pendeteksian outliers pada fitur numerik dataset.
- Melihat correlation matrix untuk mengetahui fitur yang berkorelasi sangat kecil dengan fitur target.
- Membagi dataset untuk training dan testing.
- Melakukan normalisasi dataset untuk memastikan record pada dataset tetap konsisten.

## Modelling
Model dibuat menggunakan Deep Learning dengan library TensorFlow dan Keras. Metode yang digunakan adalah Regresi dengan Deep Neural Network (DNN). Parameter pada model ini adalah sebagai berikut:
- Model : Sequential
- Loss : MAE
- Metrics : MSE
- Optimizer : Adam
- Epoch : 200

## Evaluation
Metrics evaluasi yang digunakan adalah MSE. MSE mengukur kesalahan kuadrat rata-rata dari prediksi. Untuk setiap poin, MSE menghitung selisih kuadrat antara prediksi dan target kemudian merata-rata nilai-nilai tersebut. Semakin rendah nilai MSE semakin baik modelnya, semakin tinggi nilai MSE semakin buruk modelnya, dan nilai 0 untu model yang sempurna. Nilai MSE tidak pernah negatif karena menguadratkan kesalahan prediksi individu sebelum menjumlahkannya.

- Hasil evaluasi yang didapat dari model adalah MSE 0.0703.
