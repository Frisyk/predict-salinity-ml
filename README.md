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

![Univariate Analysis](https://github.com/user-attachments/assets/64e9ed96-ccec-42cd-9d92-299853e54bad)

#### **Dari grafik di atas dapat diketahui:**  

1. **waktu_julian** (**Rentang:** 0 – 365) : Distribusi menunjukkan beberapa puncak yang menandakan data dikumpulkan pada periode tertentu dalam satu tahun.  

2. **latitude** (**Rentang:** -75 hingga 75) : Data tersebar di belahan bumi utara dan selatan dengan beberapa titik pengukuran yang lebih padat.  

3. **longitude** (**Rentang:** -60 hingga 30) : Data terkonsentrasi pada beberapa wilayah geografis tertentu.  

4. **kadar_CO₂_air** (**Rentang:** 200 – 450 ppm) : Distribusi mirip normal dengan sedikit kemiringan ke kanan.  

5. **tekanan_udara** (**Rentang:** 960 – 1025 hPa) : Distribusi mendekati normal dengan puncak sekitar 1000 hPa, menunjukkan tekanan udara standar.  

6. **suhu_air_sensor** (**Rentang:** 0 – 15°C) : Distribusi menunjukkan variasi suhu yang cukup luas, kemungkinan dipengaruhi oleh kedalaman atau lokasi pengukuran.  

7. **suhu_permukaan_laut** (**Rentang:** -2.5 – 12.5°C) : Distribusi multimodal, menandakan adanya perbedaan berdasarkan wilayah atau musim.  

8. **salinitas** (**Rentang:** 33 – 34.5 PSU) : Mayoritas data terkonsentrasi di sekitar 34 PSU, yang sesuai dengan salinitas umum air laut.  

9. **tekanan_CO₂_air** (**Rentang:** 250 – 450) : Distribusi menunjukkan adanya beberapa kelompok data dengan puncak yang signifikan.  

10. **tekanan_CO₂_udara** (**Rentang:** 385 – 415) : Lonjakan pada satu titik menunjukkan kemungkinan anomali atau pola tertentu dalam data.  

11. **fraksi_CO₂_air** (**Rentang:** 200 – 450) : Distribusi cenderung multimodal, menandakan variasi yang dipengaruhi faktor lingkungan.  

12. **fraksi_CO₂_udara** (**Rentang:** 385 – 410) : Pola distribusi serupa dengan tekanan CO₂ udara, menunjukkan adanya nilai dominan dalam rentang tertentu.  

13. **kadar_CO₂_kering** (**Rentang:** 397.5 – 410) : Distribusi simetris dengan puncak yang cukup jelas.  

14. **tekanan_air** (**Rentang:** 960 – 1020) : Distribusi mirip dengan tekanan udara, dengan mayoritas data berkumpul di sekitar nilai tertentu.  

#### **Kesimpulan:**  
- Beberapa fitur seperti **salinitas, tekanan udara, dan suhu air** memiliki distribusi mendekati normal.  
- **Latitude dan longitude** menunjukkan distribusi yang lebih tersebar dengan beberapa kepadatan tinggi di area tertentu.  
- **Tekanan dan fraksi CO₂ udara** memiliki satu lonjakan besar yang bisa mengindikasikan anomali atau efek dari faktor lingkungan tertentu.  
- **Data suhu dan CO₂** menunjukkan variasi yang dipengaruhi oleh faktor eksternal seperti lokasi geografis dan musim.  

### Multivariate Analysis

![Multivariate Analysis Fitur Numerik](https://github.com/user-attachments/assets/f25a2583-2d98-41c8-808e-483ba9bc6ec5)


Grafik diatas menunjukkan keragaman korelasi antarfitur. Dengan nilai 1 yang menunjukkan korelasi tertinggi (sangat berkorelasi).
Dapat disimpulkan fitur yang paling berkorelasi dengan salinitas adalah tekanan CO2 air, suhu air sensor, suhu permukaan laut, fraksi CO2 air dan kadar CO2 air

![salinity_vs_else](https://github.com/user-attachments/assets/3c5bceed-1d7a-4c6c-9759-9a1237b6ab8f)

fitur tekanan CO2 air, suhu air sensor, suhu permukaan laut, fraksi CO2 air dan kadar CO2 air korelasi yang positif terhadap salinitas. Korelasi positif artinya jika satu variabel meningkat, variabel lainnya (salinitas) juga meningkat.

---

## Data Preparation
Sebelum dataset diolah, fitur yang tidak dipakai akan dihapus terlebih dahulu, agar model dapat memiliki performa yang bagus. Fitur yang digunakan pada model yang dibangun yaitu fitur salinitas, tekanan udara, suhu air sensor, suhu permukaan laut, tekanan air, dan kadar CO2 air

![data frame](https://github.com/user-attachments/assets/7d28f561-b05c-4ef4-9a4c-7e8e34a9ed5b)

### Checking Missing value and Outlier

![image](https://github.com/user-attachments/assets/127aae85-3148-4458-9b8c-1b90fffc86dd)

![image](https://github.com/user-attachments/assets/a118c7a4-14ec-4dc7-b45e-2474f689b022)

Tidak terdapat missing value tetapi terdapat outlier pada dataset sehingga harus ditangani.

### Removing Outliers
untuk mengatasi outlier digunakan metode IQR. **Interquartile Range (IQR)** adalah ukuran statistik yang menunjukkan sebaran data di antara kuartil pertama (Q1) dan kuartil ketiga (Q3). IQR dihitung dengan rumus:
IQR = Q3 - Q1

![image](https://github.com/user-attachments/assets/c7d72334-19bf-47b1-8849-5d24e315f1c4)

setelah ditangani jumlah dataset menjadi 19641 sampel.

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

| Model             | Best Score | Best Params                                               |
|-------------------|-----------|-----------------------------------------------------------|
| KNN              | 0.9481     | {'n_neighbors': 5, 'weights': 'distance'}                 |
| Random Forest    | 0.9459     | {'max_depth': 32, 'n_estimators': 150, 'random_state': 42} |
| Gradient Boosting| 0.922      | {'learning_rate': 0.1, 'max_depth': 7, 'n_estimators': 150} |
| XGBoost          | 0.9294     | {'learning_rate': 0.1, 'max_depth': 7, 'n_estimators': 150} |


Berdasarkan eksperimen menggunakan GridSearchCV :

1. KNN memiliki skor tertinggi (0.9481) dengan n_neighbors = 5 dan weights = 'distance', menunjukkan bahwa model KNN dengan bobot berbasis jarak bekerja paling optimal.
2. Random Forest memiliki skor 0.9459, dengan max_depth = 32 dan n_estimators = 150, yang menunjukkan kedalaman pohon dan jumlah estimator optimal.
3. Gradient Boosting memiliki skor 0.922, dengan learning_rate = 0.1, max_depth = 7, dan n_estimators = 150, menunjukkan bahwa model ini bekerja cukup baik tetapi di bawah KNN dan Random Forest.
4. XGBoost memiliki skor 0.9294, dengan learning_rate = 0.1, max_depth = 7, dan n_estimators = 150, yang mirip dengan Gradient Boosting tetapi sedikit lebih baik.

KNN memberikan hasil terbaik, tetapi untuk dataset yang lebih besar atau kompleks, Random Forest atau XGBoost bisa lebih unggul karena lebih stabil terhadap overfitting dan lebih baik dalam menangani data noise.

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

#### Model Performance ###

|   | Model             | MSE                  | R²                  |
|---|-------------------|----------------------|----------------------|
| 0 | KNN              | 0.005886713277069045 | 0.9607243594776639  |
| 1 | Random Forest    | 0.005436011627588042 | 0.9637314018007195  |
| 2 | Gradient Boosting| 0.00811082659584525  | 0.9458852682772365  |
| 3 | XGBoost          | 0.007920471757191051 | 0.9471552992542491  |

#### Mean Squared Error (MSE) Comparison ###

| Model             | Train MSE              | Test MSE              |
|-------------------|-----------------------|-----------------------|
| KNN              | 0.0                    | 0.005886713277069045  |
| Random Forest    | 0.001059071556210185   | 0.005436011627588042  |
| Gradient Boosting| 0.0052353108813665596  | 0.00811082659584525   |
| XGBoost          | 0.005275568272595209   | 0.007920471757191051  |


### **Analisis Performa Model**  

Berdasarkan evaluasi performa model menggunakan Mean Squared Error (MSE) dan R², berikut adalah temuan utama:  

#### **Perbandingan Performa Model**  
- **Random Forest** menunjukkan performa terbaik dengan **MSE sebesar 0.0054** dan **R² sebesar 0.9637**, menandakan bahwa model ini memiliki kesalahan prediksi yang paling kecil sekaligus kemampuan prediksi yang sangat baik.  
- **KNN** juga memiliki performa tinggi dengan **MSE sebesar 0.0058** dan **R² sebesar 0.9607**, namun sedikit kalah dibandingkan Random Forest.  
- **Gradient Boosting dan XGBoost** memiliki nilai MSE yang lebih tinggi (**0.0081 dan 0.0079**), yang menunjukkan sedikit peningkatan kesalahan dibandingkan Random Forest dan KNN. Nilai R² mereka (**0.9459 dan 0.9472**) juga lebih rendah, menandakan bahwa model ini tidak menjelaskan variabilitas data sebaik dua model sebelumnya.  

#### **Analisis MSE pada Data Latih dan Uji**  
- **KNN memiliki MSE sebesar 0.0 pada data latih**, yang menunjukkan bahwa model ini **sepenuhnya menghafal data latih**, namun tetap mampu menghasilkan generalisasi yang baik pada data uji.  
- **Random Forest memiliki MSE latih yang kecil (0.0011) dibandingkan MSE uji (0.0054)**, menunjukkan bahwa model ini mampu belajar dari pola data tanpa terlalu overfitting.  
- **Gradient Boosting dan XGBoost memiliki perbedaan kecil antara MSE latih dan uji**, tetapi MSE uji mereka tetap lebih tinggi dibandingkan Random Forest, menunjukkan bahwa meskipun model ini cukup baik dalam menangkap pola data, mereka tidak seoptimal Random Forest dalam generalisasi.

### Hasil Prediksi keempat model

| y_true  | prediksi_KNN | prediksi_Random Forest | prediksi_Gradient Boosting | prediksi_XGBoost |
|---------|-------------|----------------------|--------------------------|------------------|
| 16192   | 33.440000   | 33.4                 | 33.7                     | 33.8            | 33.700001 |
| 8826    | 33.830000   | 33.8                 | 33.8                     | 33.9            | 33.900002 |
| 717     | 33.290000   | 33.2                 | 33.3                     | 33.4            | 33.400002 |
| 10846   | 33.890000   | 33.9                 | 33.9                     | 33.9            | 33.799999 |
| 5260    | 34.541404   | 34.5                 | 34.5                     | 34.5            | 34.500000 |

- Berdasarkan hasil prediksi, semua model menunjukkan performa yang baik dalam memprediksi tingkat salinitas air laut.
- Model Random Forest dan XGBoost tampaknya memberikan hasil yang paling stabil dan akurat berdasarkan sampel ini.
- Perbedaan kecil dalam prediksi menunjukkan bahwa semua model dapat digunakan untuk estimasi, tergantung pada kebutuhan spesifik dari analisis lebih lanjut.
  
---

## Conclusion
Penelitian ini berhasil menjawab problem statement yang diajukan. Faktor-faktor yang paling berpengaruh terhadap tingkat salinitas air laut telah diidentifikasi, yaitu **tekanan udara, suhu air sensor, suhu permukaan laut, dan tekanan air (korelasi positif)** serta **kadar CO₂ air (korelasi negatif)**. Selain itu, data telah melalui tahap preprocessing yang mencakup **normalisasi, pembersihan data, dan analisis multivariat**, sehingga model dapat belajar secara optimal. Dari hasil evaluasi, model terbaik untuk prediksi salinitas telah ditentukan berdasarkan performa masing-masing algoritma.  

Penelitian ini juga berhasil mencapai tujuan yang telah ditetapkan. Model **Random Forest** memiliki **MSE terendah (0.0054) dan R² tertinggi (0.9637)**, sehingga menjadi model dengan performa terbaik. Model **KNN juga menunjukkan performa yang baik**, meskipun memiliki MSE yang sedikit lebih tinggi dibandingkan Random Forest. Sementara itu, **Gradient Boosting dan XGBoost masih kompetitif**, tetapi tingkat kesalahannya lebih tinggi dibandingkan dua model terbaik tersebut.  

Dampak dari solusi yang dirancang juga terbukti efektif. **Eksplorasi dan preprocessing data** meningkatkan kualitas dataset sehingga model bekerja lebih optimal. **Pemilihan algoritma dan optimasi model** menunjukkan bahwa Random Forest adalah pilihan terbaik untuk prediksi salinitas. Selain itu, **evaluasi menggunakan MSE dan R²** berhasil mengukur tingkat kesalahan dan akurasi model, memastikan solusi yang diusulkan dapat digunakan untuk estimasi salinitas dengan tingkat kesalahan yang rendah.  

Secara keseluruhan, penelitian ini berhasil **menjawab setiap problem statement, mencapai tujuan yang diharapkan, serta membuktikan bahwa solusi yang dirancang memberikan dampak yang signifikan**. Dengan demikian, **Random Forest dapat direkomendasikan sebagai model terbaik untuk prediksi tingkat salinitas air laut**.

