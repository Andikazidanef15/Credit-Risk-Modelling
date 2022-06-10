# Credit-Risk-Modelling
## Business Understanding
Sebagai tugas akhir dari masa kontrak saya sebagai intern Data Scientist di ID/X Partners, kali ini saya akan dilibatkan dalam projek dari sebuah lending company.Saya akan berkolaborasi dengan berbagai departemen lain dalam projek ini untuk menyediakan solusi teknologi bagi company tersebut. Saya diminta untuk membangun model yang dapat memprediksi credit risk menggunakan dataset yang disediakan oleh company yang terdiri dari data pinjaman yang diterima dan yang ditolak.

Sebelum maju ke bagian analitik, akan dijelaskan terlebih dahulu apa itu credit risk modeling. Credit risk modeling adalah pemodelan yang dilakukan untuk menentukan risiko memberikan pinjaman kepada peminjam berdasarkan informasi/track record peminjam tersebut. Ada dua tipe risiko yang dihadapi oleh perusahaan pinjaman, yakni :

Peminjam dapat mengembalikan pinjamannya sesuai dengan tenggat waktu yang diberikan. Apabila pinjamannya tidak disetujui, maka perusahaan tersebut akan rugi sebesar bunga dan biaya jasa yang ditetapkan kepada peminjam tersebut.
Peminjam tidak dapat mengembalikan pinjamannya sesuai dengan tenggat waktu yang diberikan (Secara umum disebut default). Apabila pinjamannya disetujui, maka perusahaan akan rugi sebesar pinjaman, bunga dan biaya jasa yang ditetapkan kepada peminjam tersebut.
Harapannya, dengan bantuan model machine learning, kesalahan untuk memberikan/menahan pinjaman dapat ditekan secara maksimal.

## Analytic Approach
Pada bagian ini, akan dijelaskan apa yang akan saya lakukan untuk menyelesaikan permasalahan yang telah didefinisikan di bagian business understanding. Ada 3 sub bagian yang akan dijelaskan yakni :

 - Perumusan solusi
 - Menilai kelayakan solusi-solusi
 - Menentukan milestones/target-target kecil

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

Area Under Curve - Receiver Operating Characteristics (biasa disingkat AOC-ROC) adalah suatu kurva yang menggambarkan performa model dalam memprediksi variabel target. ROC adalah kurva peluangnya dan AUC menyatakan derajat separasi, digunakan untuk melihat seberapa bagus model melakukan klasifikasi variabel target. Semakin tinggi skor AUC, maka semakin baik model memprediksi variabel target tersebut.

Tetapi, performa model di atas bergantung dengan bagaimana pemrosesan datanya, terutama ada dua jenis model yang digunakan yakni model linear dan model pohon, model linear mensyaratkan harus distandarisasi datanya sementara model pohon tidak perlu menstandarisasi datanya, akan ada dua pipeline pemodelan yang berbeda untuk kedua model.

### Milestones

Langkah-langkah yang harus dilakukan untuk membuat model klasifikasi bekerja dengan baik adalah sebagai berikut :    

1. Untuk model linear (Logistic Regression, Support Vector Machine) :    
  * Isi missing values (bisa dengan median, mean atau informasi yang tertera di datanya)
  * Ubah fitur kategorikal menjadi numerik dengan One Hot Encoding,
  * Lakukan Standarisasi pada data tersebut
  * Lakukan Feature Selection dengan Statistik F untuk mengurangi fitur-fitur yang redundant

2. Untuk model pohon (Decision Tree Classifier, Random Forest Classifier) : 
  *  Isi missing values (bisa dengan median, mean atau informasi yang tertera di datanya)
  * Ubah fitur kategorikal dengan Label Encoding atau menghilangkan kata tertentu 
  * **NOTE : Tidak perlu digunakan One Hot Encoding karena justru semakin banyak fitur yang digunakan, semakin redundant fitur yang tersedia (Curse of Dimensionality), sementara model Tree akan memilih fitur yang dapat memberikan split data terbaik, makin banyak fitur, makin tidak baik split datanya**
  * Lakukan Feature Selection dengan Statistik F untuk mengurangi fitur-fitur yang redundant

## Results
Dari EDA di atas dapat diperoleh hasil analisis sebagai berikut
1. Analisis Deskriptif:
  * Terdapat kesetimbangan antara uang yang ingin dipinjam oleh peminjam dengan jumlah yang diberikan oleh pihak Lender
  * Jumlah peminjam seiring waktu menaik hingga pada tahun 2014, diperoleh jumlah peminjam yang menaik dan menurun. Selain itu, jumlah peminjam yang tidak terlambat dalam mengembalikan pinjamannya lebih banyak dibandingkan jumlah peminjam yang terlambat mengembalikan pinjamannya
  * Mayoritas peminjam meminjam uang untuk membayar hutang lainnya
  * Peminjam yang Charged Off paling banyak dibandingkan dengan kategori risiko lainnya
  * Peringkat dapat merepresentasikan kualitas peminjam tetapi tidak menjamin bahwa peminjam tersebut dapat terkategori current atau default
  * Peminjam yang Charged Off cenderung memiliki median income yang lebih rendah dibandingkan dengan kategori berisiko lainnya, sementara peminjam yang Current memiliki median income yang lebih tinggi dibandingkan peminjam berisiko
  * Peminjam peringkat G memiliki median income yang lebih tinggi dibandingkan kategori lainnya, padahal peminjam peringkat G risikonya jauh lebih tinggi dibandingkan dengan lainnya. 

2. Analisis Diagnostik :    
  * Jumlah peminjam yang menaik dan menurun saat 2014, bisa jadi disebabkan oleh perusahaan tersebut ingin memperketat syarat peminjaman atau suku bunganya dinaikkan 
  * Terdapat korelasi yang positif antara annual income peminjam dengan jumlah uang yang ingin dipinjamkan
  * Detail analisis korelasi dapat dilihat di sub bagian analisis korelasi di bagian pemodelan

3. Analisis Prediktif :
  * Diperoleh model Decision Tree Classifier adalah model terbaik dalam memprediksi variabel target dengan skor ROC-AUC 98%

