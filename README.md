# Laporan Proyek Machine Learning: Prediksi Tingkat Salinitas Air Laut  

![cover](https://github.com/user-attachments/assets/cccab2df-8a41-46ac-b195-f620c2166630)


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

## Exploratory Data analysis (EDA)

### Univariate Analysis

![Univariate Analysis](https://github.com/user-attachments/assets/a9f3104d-1793-4428-b3e3-7d4bdfd750c8)

### **Dari grafik di atas dapat diketahui:**  

1. **Waktu Julian** (Range: 0 hingga sekitar 365) 
   - Distribusi menunjukkan beberapa puncak, kemungkinan terkait dengan musim atau periode pengambilan data.

2. **Latitude** (Range: Sekitar -75 hingga 75)  
   - Distribusi menunjukkan beberapa kluster, menandakan data diambil dari berbagai lokasi.

3. **Longitude** (Range: Sekitar -75 hingga 25)
   - Distribusi bervariasi dengan beberapa puncak, menunjukkan wilayah dengan banyak pengambilan sampel.

4. **Kadar CO₂ air** (Range: Sekitar 200 hingga 500)
   - Distribusi miring ke kanan dengan kepadatan tinggi antara 300–400.

5. **Tekanan Udara** (Range: Sekitar 960 hingga 1020)
   - Distribusi menyerupai distribusi normal dengan puncak sekitar 1000.

6. **Suhu Air Sensor** (Range: 0 hingga 15)
   - Terdapat beberapa kluster data yang bisa menunjukkan kondisi lingkungan berbeda.

7. **Suhu Permukaan Laut** (Range: 0 hingga 15)
   - Pola distribusi mirip dengan suhu air sensor.

8. **Salinitas** (Range: 28 hingga 34)
   - Sebagian besar data berada di kisaran 32–34, menunjukkan karakteristik perairan tertentu.

9. **Tekanan CO₂ Air** (Range: 150 hingga 450)
   - Distribusi cenderung normal dengan puncak sekitar 300–400.

10. **Tekanan CO₂ Udara** (Range: 360 hingga 480)
    - Memiliki distribusi yang sangat terpusat dengan puncak sekitar 400.

11. **Fraksi CO₂ Air**  (Range: 150 hingga 450)
    - Pola distribusi mirip dengan tekanan CO₂ air.

12. **Fraksi CO₂ Udara** (Range: 360 hingga 480)
    - Memiliki distribusi sangat terpusat di sekitar 400.

13. **Kadar CO₂ Kering** (Range: 400 hingga 480)
    - Distribusi mirip dengan tekanan CO₂ udara dan fraksi CO₂ udara.

14. **Tekanan Air** (Range: 960 hingga 1020)
    - Pola distribusi mirip dengan tekanan udara.

Dari analisis ini, terlihat beberapa variabel memiliki distribusi normal, sementara yang lain menunjukkan kluster atau distribusi miring. Ini bisa menjadi indikasi bahwa beberapa faktor memiliki korelasi dengan lokasi atau musim.

### Multivariate Analysis

![Multivariate Analysis Fitur Numerik](https://github.com/user-attachments/assets/f25a2583-2d98-41c8-808e-483ba9bc6ec5)


Grafik diatas menunjukkan keragaman korelasi antarfitur. Dengan nilai 1 yang menunjukkan korelasi tertinggi (sangat berkorelasi).
Dapat disimpulkan fitur yang paling berkorelasi dengan salinitas adalah tekanan CO2 air, suhu air sensor, suhu permukaan laut, fraksi CO2 air dan kadar CO2 air

![salinity_vs_everyone](https://github.com/user-attachments/assets/37fdd0e0-de54-4090-8cfd-8d186d3a9c10)


fitur tekanan CO2 air, suhu air sensor, suhu permukaan laut, fraksi CO2 air dan kadar CO2 air korelasi yang positif terhadap salinitas. Korelasi positif artinya jika satu variabel meningkat, variabel lainnya (salinitas) juga meningkat.

---

## Data Preparation
Sebelum dataset diolah, fitur yang tidak dipakai akan dihapus terlebih dahulu, agar model dapat memiliki performa yang bagus. Fitur yang digunakan pada model yang dibangun yaitu fitur salinitas, tekanan CO2 air, suhu air sensor, suhu permukaan laut, fraksi CO2 air dan kadar CO2 air.

| Index | Kadar CO₂ Air | Suhu Air Sensor | Suhu Permukaan Laut | Salinitas | Tekanan CO₂ Air | Fraksi CO₂ Air |
|-------|-------------|----------------|--------------------|----------|--------------|--------------|
| 0     | 380.41      | 9.81           | 8.75               | 33.74     | 354.00       | 352.64       |
| 1     | 360.27      | 9.78           | 8.75               | 33.74     | 335.63       | 334.34       |
| 2     | 352.18      | 9.75           | 8.75               | 33.74     | 328.46       | 327.19       |
| 3     | 356.39      | 9.51           | 8.75               | 33.74     | 335.98       | 334.68       |
| 4     | 355.02      | 9.31           | 8.75               | 33.74     | 337.47       | 336.17       |


### Checking Missing value and Outlier

![missing_value](https://github.com/user-attachments/assets/32147ba1-8b33-404d-87ff-9d79889679ab)

![outliers](https://github.com/user-attachments/assets/67e591e1-2ec0-4b37-b211-7ca5398e8a97)


Tidak terdapat missing value tetapi terdapat outlier pada dataset sehingga harus ditangani.

### Removing Outliers
untuk mengatasi outlier digunakan metode IQR. **Interquartile Range (IQR)** adalah ukuran statistik yang menunjukkan sebaran data di antara kuartil pertama (Q1) dan kuartil ketiga (Q3). IQR dihitung dengan rumus:
IQR = Q3 - Q1

![removing_outliers](https://github.com/user-attachments/assets/5d7cc7e7-c37e-4fe9-9f4f-fce9bf648ca8)

setelah ditangani jumlah dataset menjadi 19879 sampel.

### Dimensionality Reduction with PCA
Fitur yang memiliki kemiripan direduksi menggunakan teknik PCA (Principal Component Analysis). Fitur yang direduksi adalah fitur Tekanan CO₂ Air dan Fraksi CO₂ Air menjadi komponen CO2; suhu air sensor dan suhu permukaan laut menjadi komponen suhu. PCA membantu menyederhanakan data tanpa kehilangan terlalu banyak informasi penting. Dengan mengurangi dimensi, mengatasi multikolinearitas, dan meningkatkan efisiensi komputasi.

### Train Test Split
Train test split adalah proses membagi data menjadi data latih dan data uji. Data latih akan digunakan untuk membangun model, sedangkan data uji akan digunakan untuk menguji performa model. Data biasanya dipisahkan dengan rasio 70:30, 80:20, 90:10. Pada proyek ini menggunakan rasio 90:10 sehingga diperoleh Jumlah data latih: 17891 dan Jumlah data uji: 1988.

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

| Index | Model             | Best Score | Best Params                                                 |
|-------|-------------------|------------|-------------------------------------------------------------|
| 0     | KNN               | 0.8811      | {'n_neighbors': 5, 'weights': 'distance'}                   |
| 1     | Random Forest     | 0.8710      | {'max_depth': 32, 'n_estimators': 100, 'random_state': 42}  |
| 2     | Gradient Boosting | 0.8455      | {'learning_rate': 0.1, 'max_depth': 7, 'n_estimators': 150} |
| 3     | XGBoost           | 0.8568      | {'learning_rate': 0.1, 'max_depth': 7, 'n_estimators': 150} |


Berdasarkan eksperimen menggunakan GridSearchCV :

1. KNN memiliki skor tertinggi (0.8811) dengan **n_neighbors = 5** dan **weights = 'distance'**, menunjukkan bahwa model KNN dengan bobot berbasis jarak bekerja paling optimal dalam skenario ini.  
2. Random Forest memiliki skor **0.871**, dengan **max_depth = 32**, **n_estimators = 100**, dan **random_state = 42**, yang menunjukkan bahwa model ini tetap kuat dengan kedalaman pohon yang cukup besar dan jumlah estimator yang optimal.  
3. Gradient Boosting memiliki skor **0.8455**, dengan **learning_rate = 0.1**, **max_depth = 7**, dan **n_estimators = 150**, menunjukkan bahwa model ini bekerja cukup baik tetapi masih berada di bawah performa KNN dan Random Forest.  
4. XGBoost memiliki skor **0.8568**, dengan **learning_rate = 0.1**, **max_depth = 7**, dan **n_estimators = 150**, yang mirip dengan Gradient Boosting tetapi menunjukkan sedikit peningkatan dalam performa.

---

## Evaluation

### **1. Mean Squared Error (MSE)**
MSE adalah metrik evaluasi yang mengukur rata-rata kuadrat selisih antara nilai sebenarnya (y_true) dan nilai prediksi (y_pred).
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

###**Hasil evaluasi model**

#### Perbandingan Performa Model

| Index | Model             | MSE                   | R²                  |
|-------|-------------------|-----------------------|----------------------|
| 0     | KNN               | 0.0188                | 0.8836               |
| 1     | Random Forest     | 0.0198                | 0.8773               |
| 2     | Gradient Boosting | 0.0237                | 0.8534               |
| 3     | XGBoost           | 0.0212                | 0.8692               |

#### Perbandingan Mean Squared Error (MSE)

| Model              | Train MSE              | Test MSE               |
|--------------------|-----------------------|------------------------|
| KNN               | 0.0000                 | 0.0188                 |
| Random Forest     | 0.0026                 | 0.0198                 |
| Gradient Boosting | 0.0107                 | 0.0237                 |
| XGBoost           | 0.0124                 | 0.0212                 |

![image](https://github.com/user-attachments/assets/e2f3a044-32d6-4dd1-8d42-db2506015dd5)


### **Analisis Performa Model**  

#### **Perbandingan Performa Model** 

- **KNN** menunjukkan performa terbaik dengan **MSE sebesar 0.0188** dan **R² sebesar 0.8836**, menandakan bahwa model ini memiliki kesalahan prediksi paling kecil serta kemampuan prediksi yang baik.
- **Random Forest** memiliki **MSE sebesar 0.0198** dan **R² sebesar 0.8773**, yang sedikit lebih rendah dibandingkan KNN tetapi tetap menunjukkan performa yang solid.
- **XGBoost** mencatat **MSE sebesar 0.0212** dan **R² sebesar 0.8692**, yang lebih baik dibandingkan Gradient Boosting tetapi masih di bawah KNN dan Random Forest.
- **Gradient Boosting** memiliki **MSE sebesar 0.0237** dan **R² sebesar 0.8534**, menunjukkan kesalahan prediksi yang lebih tinggi dibandingkan model lainnya.

#### **Analisis MSE pada Data Latih dan Uji**  

- **KNN memiliki MSE sebesar 0.0 pada data latih**, yang menunjukkan bahwa model ini sepenuhnya menghafal data latih. Namun, model ini tetap mampu melakukan generalisasi yang baik pada data uji dengan MSE sebesar 0.0188.
- **Random Forest memiliki perbedaan kecil antara MSE latih (0.0026) dan MSE uji (0.0198)**, menunjukkan bahwa model ini mampu belajar dari pola data dengan baik tanpa mengalami overfitting.
- **Gradient Boosting dan XGBoost memiliki perbedaan kecil antara MSE latih dan uji**, tetapi MSE uji mereka tetap lebih tinggi dibandingkan KNN dan Random Forest. Ini menunjukkan bahwa meskipun model ini cukup baik dalam menangkap pola data, mereka tidak seoptimal KNN dan Random Forest dalam melakukan generalisasi.


### Hasil Prediksi keempat model

| y_true | prediksi_KNN | prediksi_Random Forest | prediksi_Gradient Boosting | prediksi_XGBoost |
|--------|-------------|-----------------------|---------------------------|------------------|
| 17068  | 33.46      | 33.5                  | 33.5                      | 33.5             | 33.500000        |
| 19145  | 34.15      | 34.1                  | 34.1                      | 34.1             | 34.099998        |
| 2816   | 33.94      | 33.8                  | 33.9                      | 34.1             | 34.099998        |
| 738    | 33.60      | 33.5                  | 33.5                      | 33.7             | 33.599998        |
| 9832   | 33.59      | 33.6                  | 33.6                      | 33.6  

- **Untuk data pertama (y_true = 33.46)**, semua model memberikan prediksi yang sangat dekat dengan nilai aktual, dengan KNN memprediksi 33.5 dan model lainnya memberikan nilai yang sama, yaitu 33.5.  
- **Pada data kedua (y_true = 34.15)**, semua model memberikan hasil yang hampir identik, dengan prediksi sebesar 34.1 untuk semua model.  
- **Pada data ketiga (y_true = 33.94)**, KNN memberikan prediksi sedikit lebih rendah (33.8), sementara Random Forest menghasilkan 33.9, sedangkan Gradient Boosting dan XGBoost memberikan prediksi tertinggi, yaitu 34.1.  
- **Pada data keempat (y_true = 33.60)**, KNN dan Random Forest memprediksi 33.5, sedangkan Gradient Boosting memberikan nilai sedikit lebih tinggi (33.7), dan XGBoost hampir sama dengan nilai aktual (33.6).  
- **Pada data kelima (y_true = 33.59)**, semua model memberikan prediksi yang sangat akurat, dengan nilai yang hampir identik dengan y_true, yaitu 33.6.  

Secara keseluruhan, semua model menunjukkan performa yang baik dengan prediksi yang sangat dekat dengan nilai aktual, terutama pada kasus-kasus di mana selisih antara y_true dan prediksi sangat kecil.
  
---

## Conclusion
Penelitian ini berhasil mengidentifikasi faktor utama yang memengaruhi salinitas air laut, yaitu tekanan CO₂ air, suhu air sensor, suhu permukaan laut, fraksi CO₂ air, dan kadar CO₂ air, yang semuanya memiliki korelasi positif terhadap salinitas. Untuk meningkatkan kualitas data, dilakukan reduksi dimensi menggunakan PCA, standarisasi dengan **StandardScaler**, serta pembagian data dengan rasio **90:10**. Dari hasil eksperimen, **KNN** menunjukkan performa terbaik dengan **R² sebesar 0.8836** dan **MSE sebesar 0.0188**, diikuti oleh **Random Forest**, **XGBoost**, dan **Gradient Boosting**. Setiap solusi yang diterapkan terbukti berdampak positif, seperti **PCA yang mengurangi multikolinearitas**, **standarisasi yang meningkatkan stabilitas model**, serta **GridSearchCV yang memastikan model optimal**. Dengan demikian, penelitian ini telah berhasil mencapai semua tujuan yang ditetapkan dan memberikan solusi yang efektif dalam prediksi salinitas air laut.
