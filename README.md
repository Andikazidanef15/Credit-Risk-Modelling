# Credit-Risk-Modelling
## Business Understanding
Sebagai tugas akhir dari masa kontrak saya sebagai intern Data Scientist di ID/X Partners, kali ini saya akan dilibatkan dalam projek dari sebuah lending company.Saya akan berkolaborasi dengan berbagai departemen lain dalam projek ini untuk menyediakan solusi teknologi bagi company tersebut. Saya diminta untuk membangun model yang dapat memprediksi credit risk menggunakan dataset yang disediakan oleh company yang terdiri dari data pinjaman yang diterima dan yang ditolak.

Sebelum maju ke bagian analitik, akan dijelaskan terlebih dahulu apa itu credit risk modeling. Credit risk modeling adalah pemodelan yang dilakukan untuk menentukan risiko memberikan pinjaman kepada peminjam berdasarkan informasi/track record peminjam tersebut. Ada dua tipe risiko yang dihadapi oleh perusahaan pinjaman, yakni :

Peminjam dapat mengembalikan pinjamannya sesuai dengan tenggat waktu yang diberikan. Apabila pinjamannya tidak disetujui, maka perusahaan tersebut akan rugi sebesar bunga dan biaya jasa yang ditetapkan kepada peminjam tersebut.
Peminjam tidak dapat mengembalikan pinjamannya sesuai dengan tenggat waktu yang diberikan (Secara umum disebut default). Apabila pinjamannya disetujui, maka perusahaan akan rugi sebesar pinjaman, bunga dan biaya jasa yang ditetapkan kepada peminjam tersebut.
Harapannya, dengan bantuan model machine learning, kesalahan untuk memberikan/menahan pinjaman dapat ditekan secara maksimal.

## Analytic Approach
Pada bagian ini, akan dijelaskan apa yang akan saya lakukan untuk menyelesaikan permasalahan yang telah didefinisikan di bagian business understanding. Ada 3 sub bagian yang akan dijelaskan yakni :

Perumusan solusi
Menilai kelayakan solusi-solusi
Menentukan milestones/target-target kecil

### Perumusan Solusi
Permasalahannya adalah prediksi apakah peminjam dapat mengembalikan pinjamannya atau tidak, maka dari itu model machine learning yang akan digunakan adalah model supervised learning untuk kasus klasifikasi. Akan diuji beberapa model klasifikasi sebagai berikut :

  * Logistic Regression
  * Support Vector Machine (SVM) Classifier
  * Linear Discriminant Analysis (LDA) Classifier
  * Decision Tree Classifier
  * Random Forest Classifier
Sebelum menggunakan model tersebut, perlu diperhatikan data yang akan digunakan untuk pemodelan ini, ada 4 jenis pendekatan analitik yang akan dilakukan yakni,

  1. Analisis Deskriptif : Melihat summary statistics dari data tersebut berupa persebaran nilai target (loan_status), persebaran missing values yang ada di data tersebut, dll.
  2. Analisis Diagnostik : Melihat hubungan sebab akibat dari informasi peminjam terhadap apakah peminjam default atau tidak.

Kedua bagian di atas akan dijelaskan di sub-bagian Exploratory Data Analysis (EDA) pada bagian Data Understanding,

  3. Analisis Prediktif : Memprediksi peminjam default atau tidak dengan menggunakan model machine learning

### Menilai Kelayakan Solusi
Untuk menilai model klasifikasi yang terbaik dalam memprediksi default/tidak default, maka akan dilihat skor AUC-ROC.

Area Under Curve - Receiver Operating Characteristics (biasa disingkat AOC-ROC) adalah suatu kurva yang menggambarkan performa model dalam memprediksi variabel target. ROC adalah kurva peluangnya dan AUC menyatakan derajat separasi, digunakan untuk melihat seberapa bagus model melakukan klasifikasi variabel target. Semakin tinggi skor AUC, maka semakin baik model memprediksi variabel target tersebut. Berikut adalah kurva AOC-ROC
