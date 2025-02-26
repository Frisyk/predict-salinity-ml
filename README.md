# Laporan Proyek ML: Prediksi Tingkat Salinitas Air Laut  
### Disusun oleh: Frisnadi Nurul Huda

Untuk memenuhi submission pertama Predictive Analytic kelas Machine Learning Terapan - Dicoding Academy.
Proyek ini bertujuan untuk membuat model ML untuk memprediksi tingkat salinitas Air Laut.

---

## Domain Proyek

Sistem kehidupan di laut merupakan suatu sistem yang sangat komplek dan saling bergantungan satu sama lain baik antara organisme dengan lingkungannya.  Salah satu di antara besaran yang berperan penting dalam sistem ekologi laut adalah salinitas air laut. Beberapa jenis organisme ada yang tahan dengan perubahan nilai salinitas yang besar dan ada pula yang hanya menghendaki perubahan nilai salinitas kecil saja. Perbebedaan salinitas antara dua perairan dapat menyebabkan perbedaan yang besar dari sistem ekologi kedua perairan tersebut [[Dharma Arief, 1986]](https://www.academia.edu/download/55874237/oseana_ix13-10.pdf).

Banyak studi menjelaskan tentang peranan salinitas terhadap ekologi. Studi yang dilakukan oleh Jeriels Matatula, dkk [[2019]](https://www.academia.edu/download/69346481/pdf.pdf) menerangkan, tingkat salinitas berpengaruh terhadap laju pertumbuhan tanaman mangrove di pesisir pantai. Dharma Arif [[1986]](https://www.academia.edu/download/55874237/oseana_ix13-10.pdf) menjelaskan tentang peranan salinitas dalam pembiakkan dan pemeliharaan udang. Dalam penelitian Lisna E. Cahyani, dkk [[2023]](https://ejournal2.undip.ac.id/index.php/jkt/article/download/19817/9972) menjelaskan, bahwa selain perubahan gradient suhu, perubahan salinitas juga berperan penting dalam kedapatan fitoplakton dalam perairan.

Dalam proyek ini, peneliti meyakini bahwa salinitas berperan penting dalam memengaruhi ekosistem perairan. Tingkat salinitas dipengaruhi oleh berbagai faktor, sehingga pemahaman yang mendalam mengenai variabilitasnya menjadi hal yang krusial untuk menjaga keseimbangan ekosistem perairan. Peneliti tertarik untuk mengembangkan model machine learning yang dapat memprediksi tingkat salinitas air laut yang dipengaruhi faktor-faktor tertentu.

Referensi terkait: 
- [PREDIKSI SALINITAS AIR LAUT DENGAN DEEP NEURAL NETWORK](https://journal.binadarma.ac.id/index.php/jurnalmatrik/article/view/570) 
oleh Wiwien Widyastuti dan J. B. Budi Darmawan - Universitas Sanata Dharma

---

## Business Understanding
### Problem Statement
Dalam penelitian ini, terdapat beberapa permasalahan utama terkait prediksi tingkat salinitas air laut menggunakan machine learning, antara lain:
1. Faktor (fitur) apa saja yang paling berpengaruh terhadap tingkat salinitas air laut?
2. Bagaimana cara memproses data agar dapat dilatih dengan baik oleh model?
3. Model apa yang paling sesuai untk memprediksi tingkat salinitas air laut?

### Goals
Untuk mengatasi permasalahan di atas, penelitian ini bertujuan untuk:
1. Mengidentifikasi faktor-faktor yang berpengaruh terhadap salinitas air laut.
2. Meningkatkan kualitas data dan pemrosesan data sebelum dipakai untuk membangun model ML.
3. Mengembangkan model machine learning yang akurat agar dapat memprediksi tingkat salinitas air laut dengan baik.

### Solution Statement
Untuk mencapai tujuan tersebut, penelitian ini mengusulkan beberapa solusi:
1. Eksplorasi dan Preprocessing Data
Dengan mengumpulkan dataset dari sumber yang terpercaya, menganalisis data dengan melakukan univariate analysis dan multivariate analysis. Selanjutnya melakukan pra-pemprosesan data seperti normalisasi dan pembersihan data untuk mengatasi missing values dan outliers.
2. Pemilihan Algoritma dan Optimasi Model
Menggunakan berbagai algoritma machine learning seperti K-Nearest Neighbour, Random Forest, Gradient Boosting, atau XGBoost untuk menentukan model yang paling optimal. Melakukan hyperparameter tuning menggunakan teknik seperti Grid Search untuk meningkatkan performa model.
3. Evaluasi Model dengan Metrik yang Tepat
Menggunakan metrik evaluasi seperti Mean Square Error (MSE) dan R2 score untuk menilai kualitas prediksi model.

---

## Data Understanding
Pada proyek ini peneliti menggunakan dataset ["Underway pCO₂ and Ocean Data"](https://www.kaggle.com/datasets/patricklford/underway-pco-and-ocean-data-rv-j-clark-ross) dari R/V J. Clark Ross yang diperoleh dari situs [Kaggle](https://www.kaggle.com). Berikut informasi pada dataset :
+ Dataset memiliki format CSV (Comma-Seperated Vaslues).
+ Dataset memiliki 24562 sample dengan 16 fitur.
+ Dataset memiliki 14 fitur bertipe float64 dan 2 fitur bertipe object.
### Variabel-variabel/fitur pada "Underway pCO₂ and Ocean Data" dataset adalah sebagai berikut:
1. **JD_GMT** *(Julian Date - Greenwich Mean Time)*  
   Format waktu dalam **Julian Date**, yang digunakan dalam astronomi dan ilmiah untuk menyatakan tanggal dalam satuan hari sejak 1 Januari 4713 SM.  
2. **DATE_UTC__ddmmyyyy** *(Tanggal UTC - Hari/Bulan/Tahun)*  
   Tanggal pencatatan data dalam format **ddmmyyyy** (misalnya, *01012022* berarti 1 Januari 2022).  
3. **TIME_UTC_hh:mm:ss** *(Waktu UTC - Jam:Menit:Detik)*  
   Waktu pencatatan dalam **Coordinated Universal Time (UTC)** dalam format jam:menit:detik.  
4. **LAT_dec_degree** *(Latitude dalam Derajat Desimal)*  
   Posisi lintang lokasi pengambilan data dalam **derajat desimal**.  
   **Nilai positif** → Belahan bumi **utara** (N).  
   **Nilai negatif** → Belahan bumi **selatan** (S).  
5. **LONG_dec_degree** *(Longitude dalam Derajat Desimal)*  
   Posisi bujur dalam **derajat desimal**.  
   **Nilai positif** → Bujur **timur** (E).  
   **Nilai negatif** → Bujur **barat** (W).  
6. **xCO2_equ[umol/mol]** *(Konsentrasi CO₂ pada Keseimbangan - Mikromol per Mol)*  
   Konsentrasi **karbon dioksida (CO₂)** dalam air yang telah mencapai **keseimbangan dengan atmosfer**.  
   Diukur dalam **mikromol per mol (μmol/mol)**.  
7. **Patm [hPa]** *(Tekanan Atmosfer dalam Hektopascal)*  
   Tekanan atmosfer di lokasi pengukuran dalam **hektopascal (hPa)**.  
   Tekanan standar di permukaan laut biasanya sekitar **1013 hPa**.  
8. **Tequ [deg.C]** *(Suhu Keseimbangan dalam Derajat Celcius)*  
   Suhu pada titik **keseimbangan gas-air** dalam **derajat Celsius**.  
9. **SST [deg.C]** *(Sea Surface Temperature - Suhu Permukaan Laut dalam Derajat Celsius)*  
   Suhu permukaan air laut dalam **derajat Celsius**.  
   Parameter penting untuk mempelajari **perubahan iklim dan sirkulasi laut**.  
10. **Sal** *(Salinitas atau Kadar Garam dalam PSU - Practical Salinity Unit)*  
   Mengukur **kadar garam dalam air laut**.  
   Satuan yang digunakan biasanya **PSU (Practical Salinity Unit)**, di mana air laut rata-rata memiliki salinitas **sekitar 35 PSU**.  
11. **pCO2_sw[uatm]** *(Tekanan Parsial CO₂ di Air Laut dalam Mikro Atmosfer)*  
   **Tekanan parsial karbon dioksida (CO₂) dalam air laut** dalam satuan **μatm (mikro atmosfer)**.  
   Semakin tinggi nilai ini, semakin banyak CO₂ yang terlarut dalam air laut.  
12. **pCO2_atm[uatm]** *(Tekanan Parsial CO₂ di Atmosfer dalam Mikro Atmosfer)*  
   **Tekanan parsial CO₂ di atmosfer** dalam satuan **μatm**.  
   Digunakan untuk membandingkan konsentrasi CO₂ antara laut dan atmosfer.  
13. **fCO2_sw[uatm]** *(Tekanan Parsial CO₂ yang Disesuaikan dengan Faktor Aktivitas di Laut)*  
   Sama seperti **pCO2_sw**, tetapi dikoreksi dengan faktor aktivitas untuk memperhitungkan kelarutan CO₂ di air laut.  
14. **fCO2_atm[uatm]** *(Tekanan Parsial CO₂ yang Disesuaikan dengan Faktor Aktivitas di Atmosfer)*  
   Sama seperti **pCO2_atm**, tetapi dikoreksi dengan faktor aktivitas untuk memperhitungkan pengaruh tekanan dan suhu udara.  
15. **xCO2atm_dry[umol/mol]** *(Konsentrasi CO₂ Kering di Atmosfer dalam Mikromol per Mol)*  
   **Konsentrasi karbon dioksida di udara kering** dalam **μmol/mol**.  
   Ini adalah nilai konsentrasi CO₂ setelah menghilangkan pengaruh kelembaban udara.  
16. **Pequ [hPa]** *(Tekanan di Kamar Keseimbangan dalam Hektopascal)*  
   Tekanan udara dalam **ruang keseimbangan** di mana pengukuran pCO₂ dilakukan.  
   Digunakan untuk memperbaiki dan menyesuaikan data pCO₂ agar lebih akurat.

**Nama fitur-fitur tersebut kemudian diubah kedalam bahasa indonesia agar memudahkan pemahaman data.**

### Removing Missing value dan Outlier

Terdapat missing value dan outlier pada dataset sehingga harus ditangani.

![missing value](https://github.com/user-attachments/assets/a726f3d8-18c2-40b8-88c9-cad593b0036f)

Untuk missing value digunakan Model Prediksi untuk mengisi nilai yang hilang.

Sedangkan untuk mengatasi outlier digunakanlah metode IQR

![Handling Outlier](https://github.com/user-attachments/assets/9e3603de-e778-42e4-8fbc-ea075922e794)

setelah ditangani jumlah dataset menjadi 16576 sampel.

### Univariate Analysis

![Univariate Analysis Fitur Numerik](https://github.com/user-attachments/assets/65865f8b-2a16-4b53-be8c-fe4704a28863)

Dari grafik diatas dapat diketahui rentang nilai masing-masing fitur yang beragam.

### Multivariate Analysis

![Multivariate Analysis Fitur Numerik](https://github.com/user-attachments/assets/5024b691-fab6-45d8-b367-51ba7e37b317)

Grafik diatas menunjukkan keragaman korelasi antarfitur. Dengan nilai 1 yang menunjukkan korelasi tertinggi (sangat berkorelasi).
Dapat disimpulkan fitur yang paling berkorelasi dengan salinitas adalah tekanan udara, suhu air sensor, suhu permukaan laut, tekanan air, dan kadar CO2 air

![salinity_grafik](https://github.com/user-attachments/assets/2c97b2a8-777a-4293-9fbf-0ac1bdad40d5)

fitur tekanan udara, suhu air sensor, suhu permukaan laut, tekanan air memiliki korelasi yang positif terhadap salinitas. Sedangkan kadar CO2 air berkorelasi yang negatif.

---

## Data Preparation
Sebelum dataset diolah, fitur yang tidak dipakai akan dihapus terlebih dahulu, agar model dapat memiliki performa yang bagus. Fitur yang digunakan pada model yang dibangun yaitu fitur salinitas, tekanan udara, suhu air sensor, suhu permukaan laut, tekanan air, dan kadar CO2 air

![data frame](https://github.com/user-attachments/assets/7d28f561-b05c-4ef4-9a4c-7e8e34a9ed5b)

### Dimensionality Reduction with PCA
Fitur yang memiliki kemiripan direduksi menggunakan teknik PCA (Principal Component Analysis). Fitur yang direduksi adalah fitur tekanan udara dan tekanan air menjadi komponen tekanan; suhu air sensor dan suhu permukaan laut menjadi komponen suhu. PCA membantu menyederhanakan data tanpa kehilangan terlalu banyak informasi penting. Dengan mengurangi dimensi, mengatasi multikolinearitas, dan meningkatkan efisiensi komputasi.

### Train Test Split
Train test split adalah proses membagi data menjadi data latih dan data uji. Data latih akan digunakan untuk membangun model, sedangkan data uji akan digunakan untuk menguji performa model. Data biasanya dipisahkan dengan rasio 70:30, 80:20, 90:10. Pada proyek ini menggunakan rasio 90:10 sehingga diperoleh Jumlah data latih: 14918 dan Jumlah data uji: 1658.

### Standarization
Algoritma machine learning memiliki performa lebih baik dan konvergen lebih cepat ketika dimodelkan pada data dengan skala relatif sama atau mendekati distribusi normal. Proses scaling dan standarisasi membantu untuk membuat fitur data menjadi bentuk yang lebih mudah diolah oleh algoritma. Proyek ini menggunakan teknik StandarScaler dari library Scikitlearn untuk standarisasi.

---

## Modeling
### **1. K-Nearest Neighbors (KNN)**
K-Nearest Neighbors (KNN) adalah algoritma non-parametrik yang digunakan untuk regresi dan klasifikasi. Algoritma ini bekerja dengan mencari sejumlah **K** tetangga terdekat berdasarkan metrik jarak tertentu (misalnya, **Euclidean distance**).
- **Kelebihan**: Mudah diimplementasikan, bekerja baik pada dataset kecil.  
- **Kekurangan**: Lambat untuk dataset besar, sensitif terhadap skala data.  

### **2. Random Forest (RF)**
Random Forest adalah algoritma berbasis **ensemble learning** yang menggunakan banyak **decision tree** untuk membuat prediksi. Model ini bekerja dengan cara: 1. Membuat beberapa **decision tree** dari subset data yang berbeda (Bootstrap Sampling). 2. Setiap pohon memberikan prediksi, dan hasil akhir ditentukan berdasarkan rata-rata prediksi dari semua pohon (**bagging**).
- **Kelebihan**: Tidak mudah overfitting, dapat menangani fitur yang banyak.  
- **Kekurangan**: Lambat untuk prediksi real-time.  

### **3. Gradient Boosting (GB)**
Gradient Boosting adalah algoritma boosting yang membangun pohon keputusan secara **iteratif** dengan cara **memperbaiki kesalahan dari model sebelumnya**. Berbeda dengan Random Forest yang menggunakan **bagging**, Gradient Boosting menggunakan **boosting** di mana setiap pohon baru berusaha mengurangi error dari model sebelumnya. 
- **Kelebihan**: Performa tinggi, menangani data kompleks.  
- **Kekurangan**: Rentan overfitting, lambat dalam training.  

### **4. XGBoost**
XGBoost adalah varian **Gradient Boosting** yang dioptimalkan untuk performa tinggi. Algoritma ini lebih cepat dan lebih efisien dalam menangani **overfitting** serta mampu mengolah data besar dengan lebih baik dibandingkan Gradient Boosting biasa.
- **Kelebihan**: Cepat, lebih baik dalam menangani overfitting.  
- **Kekurangan**: Perlu tuning parameter yang lebih kompleks.  

### **Proses Improvement (Hyperparameter Tuning) dengan Grid Search**
GridSearchCV adalah metode pencarian parameter terbaik (hyperparameter tuning) menggunakan pencarian grid (grid search) dengan cross-validation.
Pada GridSearchCV, parameter yang diuji untuk setiap model:
- **KNN**: `n_neighbors` dan `weights`.  
- **RF, GB, XGBoost**: `n_estimators`, `max_depth`, dan `learning_rate`.  

![image](https://github.com/user-attachments/assets/3b306975-673b-42c1-8604-65a6483681d0)

Berdasarkan eksperimen menggunakan GridSearchCV :

1. KNN (0.9475) → Performa terbaik dengan n_neighbors=5 dan weights='distance'.
2. Random Forest (0.9434) → Performa hampir setara, tetapi lebih stabil untuk data besar.
3. Gradient Boosting (0.9273) → Model boosting yang kuat tetapi kalah sedikit dari XGBoost.
4. XGBoost (0.9303) → Model yang sangat powerful tetapi sedikit lebih rendah dari KNN dan RF.

KNN memberikan hasil terbaik, tetapi untuk dataset yang lebih besar atau kompleks, Random Forest atau XGBoost bisa lebih unggul karena lebih stabil terhadap overfitting dan lebih baik dalam menangani data noise.

---

## Evaluation

### **1. Mean Squared Error (MSE)**
MSE mengukur rata-rata kesalahan kuadrat antara nilai prediksi dan nilai aktual.  
**Formula MSE:**  

![MSE](https://github.com/user-attachments/assets/130f0de2-064a-4863-b6d8-687cbe63c645)

- **Lebih kecil MSE = lebih baik**  
- **Sensitif terhadap outlier** karena nilai error dikuadratkan.  

### **2. R-Squared (R²)**
R² mengukur seberapa baik model menjelaskan variasi dalam data.  
**Formula R²:**  

![R2](https://github.com/user-attachments/assets/e5f86371-c897-4647-a327-1896f573a9ac)

di mana:

![image](https://github.com/user-attachments/assets/3a3d44e1-d2d4-4339-a328-ee11c4a28e6b)
 

**Interpretasi R²:**  
- **\( R² = 1 \)** → Model sempurna.  
- **\( R² = 0 \)** → Model tidak lebih baik dari rata-rata.  
- **\( R² < 0 \)** → Model lebih buruk dari tebakan rata-rata.  

**Hasil evaluasi model**

![MSE_R2](https://github.com/user-attachments/assets/6c5cc117-c914-4380-a4aa-5b6fcbe0adca)

![MSE train test](https://github.com/user-attachments/assets/56fa80dc-28ef-4121-aaf0-aa96b020d6b9)

**Hasil evaluasi menunjukkan model Random Forest memberikan performa terbaik dibandingkan algoritma lain dalam proyek ini.**

