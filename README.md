# Laporan Proyek *Machine Learning* - Alfendio Alif Faudisyah

## Domain Proyek
Pada era modern ini kebutuhan teknologi berbasis komputer telah menjadi kebutuhan utama bagi masyarakat. Salah satu perangkat komputer yang banyak digunakan adalah laptop. Kebutuhan akan laptop tersebut memunculkan bisnis jual beli pada laptop. Orang awam banyak yang tidak mengetahui mengenai harga laptop karena tiap laptop memiliki spesifikasi yang berbeda. Oleh karena itu dibuatlah suatu sistem yang dapat memprediksi harga laptop sehingga dapat memudahkan pembeli laptop untuk mengetahui harga laptop.

## *Business Understanding*
### *Problem Statements*
- Bagaimana cara mengetahui harga laptop berdasarkan spesifikasinya?

### *Goals*
- Membuat sistem yang dapat memprediksi harga laptop berdasarkan spesifikasi.

## *Data Understanding*
Dataset didapatkan dari [Kaggle](https://www.kaggle.com/datasets/muhammetvarl/laptop-price).

### Nama Dataset
- Laptop Price

### Jumlah Dataset
Dataset berisi 12 kolom dan 1301 baris.

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

## *Data Preparation*
- Melakukan pendeteksian *outliers* pada fitur numerik dataset menggunakan boxplot.
- Melakukan *drop outliers*.
- Membuat batas bawah dan atas. Batas bawah = Q1 - 1.5 * IQR dan batas atas = Q3 + 1.5 * IQR.
- Melihat histogram fitur numerik menggunakan fitur numerik.

![output numerical features](https://user-images.githubusercontent.com/73519055/209517490-31de5e5a-63f4-4acc-bec7-2eedbc7fe305.png)


- Mengamati hubungan antar fitur numerik menggunakan fungsi pairplot.

![pairplot](https://user-images.githubusercontent.com/73519055/209517583-f489a09a-8909-43c9-bc3a-e8fd856c4068.png)


- Mengevaluasi skor korelasi menggunakan fungsi corr.
- Melihat *correlation matrix* untuk mengetahui fitur yang berkorelasi sangat kecil dengan fitur target menggunakan fungsi heatmap. Dapat dilihat fitur 'Weight' memiliki korelasi yang sangat kecil yaitu 0.04.

![output correlation matrix](https://user-images.githubusercontent.com/73519055/209517260-78154877-3201-41a8-ac72-30a384dbaf7c.png)

- Melakukan drop fitur 'Weight' yang memiliki korelasi kecil dengan fitur target.
- Membagi dataset untuk training 80% dan testing 20%.
- Melakukan normalisasi dataset untuk memastikan *record* pada dataset tetap konsisten.
- Membuat lapisan normalisasi dengan tf.keras.layers.
- Menyesuaikan lapisan pra-pemrosesan ke data menggunakan fungsi adapt.

## *Modelling*
Model dibuat menggunakan *Deep Learning* dengan library TensorFlow dan Keras. Metode yang digunakan adalah Regresi dengan *Deep Neural Network* (DNN). Model DNN ini bekerja dari *node layer*, dimana *node* tiap *layer* terhubung dengan *node* lain yang saling berdekatan. *Layer* yang digunakan adalah *Normalization* sebagai *input layer*, dua lapisan *Dense* dengan activation ReLU sebagai *hidden layer*, *DropOut* untuk mengurangi *overfitting*, dan *Dense* sebagai output layer. Fungsi aktivasi ReLU sendiri adalah fungsi aktivasi non-linier sederhana yang dapat melakukan *gradient descent* dengan cepat. Tahapan yang dilakukan dalam *modelling* adalah membangun model *sequential* dengan *layers* yang telah disebutkan, melakukan *compile* model dengan mengatur *loss*, *metric*, dan *optimizer*, kemudian model *fit* untuk proses *training*. 

### Rangkuman Model
![image](https://user-images.githubusercontent.com/73519055/209514627-4c22d1f7-c452-4afd-a83e-2297b641b933.png)

### Parameter model :
- Model : *Sequential*
- Loss : MAE
- Metrics : MSE
- Optimizer : Adam. Adam (*Adaptive Moment Estimation*) adalah metode learning rate adaptif yang menghitung learning rate individu untuk parameter yang berbeda.
- Epoch : 200

## *Evaluation*
*Metric* evaluasi yang digunakan adalah MSE. MSE mengukur kesalahan kuadrat rata-rata dari prediksi. Untuk setiap poin, MSE menghitung selisih kuadrat antara prediksi dan target kemudian merata-rata nilai-nilai tersebut. Semakin rendah nilai MSE semakin baik modelnya, semakin tinggi nilai MSE semakin buruk modelnya, dan nilai 0 untu model yang sempurna. Nilai MSE tidak pernah negatif karena menguadratkan kesalahan prediksi individu sebelum menjumlahkannya.

### Visualisasi asil *training loss*
![output mae](https://user-images.githubusercontent.com/73519055/209512579-8066bc46-0650-41ef-bfd9-4a2840915288.png)

### Visualisasi hasil *training mse**
![output mse](https://user-images.githubusercontent.com/73519055/209512693-cd5dc8da-2e74-462e-a5cc-be1ced4ac5de.png)

Hasil yang didapat dari visualisasi training adalah loss: 0.2671, val_loss: 0.1902, mse: 0.1113, dan val_mse: 0.0679.

### Hasil Evaluasi
Dilakukan evaluasi pada model menggunakan data *testing* dengan menggunakan fungsi model.evaluate. Hasil penerapan dengan *metric* evaluasi yang digunakan pada gambar visualisasi hasil training adalah loss: 0.2053 dan mse: 0.0703. Dilihat dari nilai MSE model sudah dapat dibilang baik karena memiliki nilai yang cukup kecil.

