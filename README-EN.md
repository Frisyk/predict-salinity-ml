# Machine Learning Project Report: Predicting Seawater Salinity Levels  

![cover](https://github.com/user-attachments/assets/cccab2df-8a41-46ac-b195-f620c2166630)

### Prepared by: Frisnadi Nurul Huda

This report is submitted as the first submission for the Predictive Analytics course in the Applied Machine Learning class at Dicoding Academy. The objective of this project is to develop a machine learning model to predict seawater salinity levels.

---

## Project Domain

Marine life systems are highly complex and interdependent, involving interactions between organisms and their environment. One of the crucial factors influencing marine ecological systems is seawater salinity. Some marine organisms can tolerate significant changes in salinity levels, while others require minimal variations. Differences in salinity between two bodies of water can lead to significant ecological differences between them [[Dharma Arief, 1986]](https://www.academia.edu/download/55874237/oseana_ix13-10.pdf).

Numerous studies have explored the role of salinity in ecology. Research conducted by Jeriels Matatula et al. [[2019]](https://www.academia.edu/download/69346481/pdf.pdf) indicates that salinity levels influence the growth rate of mangrove plants along coastal areas. Dharma Arief [[1986]](https://www.academia.edu/download/55874237/oseana_ix13-10.pdf) discusses the role of salinity in shrimp breeding and maintenance. Additionally, a study by Lisna E. Cahyani et al. [[2023]](https://ejournal2.undip.ac.id/index.php/jkt/article/download/19817/9972) highlights that, besides temperature gradients, salinity variations play a crucial role in phytoplankton abundance in aquatic ecosystems.

In this project, the researcher acknowledges the significance of salinity in shaping aquatic ecosystems. Salinity levels are influenced by various factors, making it essential to understand their variability to maintain ecological balance. The researcher aims to develop a machine learning model capable of predicting seawater salinity levels based on influencing factors.

Related references:
- [PREDICTING SEAWATER SALINITY USING DEEP NEURAL NETWORK](https://journal.binadarma.ac.id/index.php/jurnalmatrik/article/view/570) by Wiwien Widyastuti and J. B. Budi Darmawan - Universitas Sanata Dharma

---

## Business Understanding
### Problem Statement
This study aims to address several key issues related to predicting seawater salinity levels using machine learning:
1. What are the most influential factors (features) affecting seawater salinity levels?
2. How should the data be processed to optimize model training?
3. Which machine learning model is best suited for predicting seawater salinity levels?

### Goals
To address these issues, this study aims to:
1. Identify the key factors influencing seawater salinity levels.
2. Improve data quality and preprocessing before using it to train machine learning models.
3. Develop an accurate machine learning model capable of effectively predicting seawater salinity levels.

### Solution Statement
To achieve these objectives, the study proposes the following solutions:
1. **Data Exploration and Preprocessing**
   - Collect datasets from reliable sources and analyze data using univariate and multivariate analysis.
   - Perform data preprocessing such as normalization and cleaning to handle missing values and outliers.
2. **Algorithm Selection and Model Optimization**
   - Utilize various machine learning algorithms such as K-Nearest Neighbors, Random Forest, Gradient Boosting, or XGBoost to determine the most optimal model.
   - Conduct hyperparameter tuning using techniques like Grid Search to enhance model performance.
3. **Model Evaluation Using Appropriate Metrics**
   - Employ evaluation metrics such as Mean Squared Error (MSE) and R² score to assess model prediction quality.

---

## Data Understanding
For this project, the researcher utilized the dataset titled ["Underway pCO₂ and Ocean Data"](https://www.kaggle.com/datasets/patricklford/underway-pco-and-ocean-data-rv-j-clark-ross) from R/V J. Clark Ross, obtained from [Kaggle](https://www.kaggle.com). The dataset details are as follows:
+ The dataset is in CSV (Comma-Separated Values) format.
+ It contains **24,562 samples** with **16 features**.
+ It includes **14 features** of type `float64` and **2 features** of type `object`.

### Features in the "Underway pCO₂ and Ocean Data" Dataset:
1. **JD_GMT (Julian Date - Greenwich Mean Time)**  
   - Time format in **Julian Date**, commonly used in astronomy and scientific applications to represent dates in days since January 1, 4713 BC.
2. **DATE_UTC_ddmmyyyy (UTC Date - Day/Month/Year)**  
   - Date of data recording in the format **ddmmyyyy** (e.g., *01012022* represents January 1, 2022).
3. **TIME_UTC_hh:mm:ss (UTC Time - Hour:Minute:Second)**  
   - Time of recording in **Coordinated Universal Time (UTC)** format (hh:mm:ss).
4. **LAT_dec_degree (Latitude in Decimal Degrees)**  
   - Latitude of the data collection site in **decimal degrees**.
   - **Positive values** → **Northern Hemisphere (N)**.
   - **Negative values** → **Southern Hemisphere (S)**.
5. **LONG_dec_degree (Longitude in Decimal Degrees)**  
   - Longitude of the data collection site in **decimal degrees**.
   - **Positive values** → **Eastern Hemisphere (E)**.
   - **Negative values** → **Western Hemisphere (W)**.
6. **xCO₂_equ[umol/mol] (Equilibrium CO₂ Concentration - Micromol per Mol)**  
   - Concentration of **carbon dioxide (CO₂)** in water at **equilibrium with the atmosphere**.
   - Measured in **micromoles per mole (μmol/mol)**.
7. **Patm [hPa] (Atmospheric Pressure in Hectopascals)**  
   - Atmospheric pressure at the measurement location, measured in **hectopascals (hPa)**.
   - Standard sea-level pressure is approximately **1013 hPa**.
8. **Tequ [°C] (Equilibrium Temperature in Celsius)**  
   - Temperature at the **gas-water equilibrium point**, measured in **degrees Celsius**.
9. **SST [°C] (Sea Surface Temperature in Celsius)**  
   - Surface seawater temperature in **degrees Celsius**.
10. **Sal (Salinity or Salt Content in PSU - Practical Salinity Unit)**  
    - Measures **salt concentration in seawater**.
    - Typically expressed in **PSU (Practical Salinity Unit)**, where average seawater salinity is around **35 PSU**.
11. **pCO₂_sw[uatm] (Partial Pressure of CO₂ in Seawater - Micro Atmospheres)**  
    - **Partial pressure of carbon dioxide (CO₂) in seawater**, measured in **μatm (micro-atmospheres)**.
12. **pCO₂_atm[uatm] (Partial Pressure of CO₂ in Atmosphere - Micro Atmospheres)**  
    - **Partial pressure of CO₂ in the atmosphere**, measured in **μatm**.
13. **fCO₂_sw[uatm] (CO₂ Partial Pressure Adjusted for Activity in Seawater)**  
    - Similar to **pCO₂_sw**, but adjusted with an activity factor to account for CO₂ solubility in seawater.
14. **fCO₂_atm[uatm] (CO₂ Partial Pressure Adjusted for Activity in Atmosphere)**  
    - Similar to **pCO₂_atm**, but corrected with an activity factor for pressure and temperature effects.

---

## Exploratory Data Analysis (EDA)

### Univariate Analysis

![Univariate Analysis](https://github.com/user-attachments/assets/a9f3104d-1793-4428-b3e3-7d4bdfd750c8)

### **Insights from the above graph:**  

1. **Julian Time** (Range: 0 to approximately 365)  
   - The distribution shows several peaks, possibly related to seasonal variations or data collection periods.

2. **Latitude** (Range: Approximately -75 to 75)  
   - The distribution indicates several clusters, suggesting data was collected from multiple locations.

3. **Longitude** (Range: Approximately -75 to 25)  
   - The distribution varies with multiple peaks, highlighting areas with high sampling frequency.

4. **Water CO₂ Concentration** (Range: Approximately 200 to 500)  
   - The distribution is right-skewed, with a high density between 300–400.

5. **Air Pressure** (Range: Approximately 960 to 1020)  
   - The distribution resembles a normal distribution, peaking around 1000.

6. **Sensor Water Temperature** (Range: 0 to 15)  
   - There are multiple data clusters, possibly indicating different environmental conditions.

7. **Sea Surface Temperature** (Range: 0 to 15)  
   - The distribution pattern is similar to sensor water temperature.

8. **Salinity** (Range: 28 to 34)  
   - Most data points fall within 32–34, indicating specific water characteristics.

9. **Water CO₂ Pressure** (Range: 150 to 450)  
   - The distribution tends to be normal, peaking around 300–400.

10. **Air CO₂ Pressure** (Range: 360 to 480)  
    - It has a highly concentrated distribution, peaking around 400.

11. **Water CO₂ Fraction** (Range: 150 to 450)  
    - The distribution pattern is similar to water CO₂ pressure.

12. **Air CO₂ Fraction** (Range: 360 to 480)  
    - It has a highly centralized distribution around 400.

13. **Dry CO₂ Concentration** (Range: 400 to 480)  
    - The distribution is similar to air CO₂ pressure and air CO₂ fraction.

14. **Water Pressure** (Range: 960 to 1020)  
    - The distribution pattern is similar to air pressure.

This analysis shows that some variables follow a normal distribution, while others exhibit clustering or skewness. This could indicate correlations with location or seasonal factors.

### Multivariate Analysis

![Multivariate Analysis of Numerical Features](https://github.com/user-attachments/assets/f25a2583-2d98-41c8-808e-483ba9bc6ec5)

The above graph illustrates the correlation among features, where a value of 1 represents the highest correlation (strongly correlated). The features most correlated with salinity include water CO₂ pressure, sensor water temperature, sea surface temperature, water CO₂ fraction, and water CO₂ concentration.

![salinity_vs_everyone](https://github.com/user-attachments/assets/37fdd0e0-de54-4090-8cfd-8d186d3a9c10)

The features water CO₂ pressure, sensor water temperature, sea surface temperature, water CO₂ fraction, and water CO₂ concentration exhibit a positive correlation with salinity. A positive correlation means that when one variable increases, the other variable (salinity) also increases.

---

## Data Preparation  
Before processing the dataset, unnecessary features were removed to enhance model performance. The selected features for modeling include salinity, water CO₂ pressure, sensor water temperature, sea surface temperature, water CO₂ fraction, and water CO₂ concentration.

| Index | Water CO₂ Concentration | Sensor Water Temperature | Sea Surface Temperature | Salinity | Water CO₂ Pressure | Water CO₂ Fraction |
|-------|------------------------|--------------------------|------------------------|----------|--------------------|--------------------|
| 0     | 380.41                 | 9.81                     | 8.75                   | 33.74     | 354.00             | 352.64             |
| 1     | 360.27                 | 9.78                     | 8.75                   | 33.74     | 335.63             | 334.34             |
| 2     | 352.18                 | 9.75                     | 8.75                   | 33.74     | 328.46             | 327.19             |
| 3     | 356.39                 | 9.51                     | 8.75                   | 33.74     | 335.98             | 334.68             |
| 4     | 355.02                 | 9.31                     | 8.75                   | 33.74     | 337.47             | 336.17             |

### Checking Missing Values and Outliers  

![Missing Values](https://github.com/user-attachments/assets/32147ba1-8b33-404d-87ff-9d79889679ab)

![Outliers](https://github.com/user-attachments/assets/67e591e1-2ec0-4b37-b211-7ca5398e8a97)

No missing values were detected, but the dataset contains outliers that must be handled.

### Removing Outliers  
To address outliers, the **Interquartile Range (IQR)** method was applied. IQR is a statistical measure that describes the spread of the data between the first quartile (Q1) and the third quartile (Q3), calculated as:  
**IQR = Q3 - Q1**

![Removing Outliers](https://github.com/user-attachments/assets/5d7cc7e7-c37e-4fe9-9f4f-fce9bf648ca8)

After handling outliers, the dataset was reduced to 19,879 samples.

### Dimensionality Reduction with PCA  
Features with high similarity were reduced using **Principal Component Analysis (PCA)**. The transformed features include:  
- Water CO₂ Pressure and Water CO₂ Fraction → **CO₂ Component**  
- Sensor Water Temperature and Sea Surface Temperature → **Temperature Component**  

PCA helps simplify data while preserving essential information, reducing dimensionality, handling multicollinearity, and improving computational efficiency.

### Train-Test Split  
Train-test splitting is the process of dividing the dataset into training and testing sets. The training set is used to build the model, while the testing set evaluates model performance. Common split ratios include 70:30, 80:20, and 90:10. In this project, a **90:10 split** was applied, resulting in:  
- **Training data:** 17,891 samples  
- **Testing data:** 1,988 samples  

### Standardization  
Machine learning algorithms perform better and converge faster when trained on data with a similar scale or near-normal distribution. **Scaling and standardization** ensure that data features are transformed into a more machine-friendly format. This project uses **StandardScaler** from the Scikit-Learn library for standardization.

---

## Modeling
### **1. K-Nearest Neighbors (KNN)**
K-Nearest Neighbors (KNN) is a non-parametric algorithm used for regression and classification. This algorithm works by finding **K** nearest neighbors based on a specific distance metric (e.g., **Euclidean distance**).
- **Advantages**: Easy to implement, works well on small datasets.  
- **Disadvantages**: Slow for large datasets, sensitive to data scaling.  

### **2. Random Forest (RF)**
Random Forest is an **ensemble learning** algorithm that uses multiple **decision trees** to make predictions. The model works by:  
1. Creating multiple **decision trees** from different data subsets (Bootstrap Sampling).  
2. Each tree provides a prediction, and the final result is determined based on the average prediction from all trees (**bagging**).
- **Advantages**: Less prone to overfitting, can handle many features.  
- **Disadvantages**: Slow for real-time predictions.  

### **3. Gradient Boosting (GB)**
Gradient Boosting is a boosting algorithm that builds decision trees **iteratively** by **correcting errors from the previous model**. Unlike Random Forest, which uses **bagging**, Gradient Boosting employs **boosting**, where each new tree attempts to reduce the error from the previous model.
- **Advantages**: High performance, handles complex data well.  
- **Disadvantages**: Prone to overfitting, slow training process.  

### **4. XGBoost**
XGBoost is an optimized variant of **Gradient Boosting** designed for high performance. This algorithm is faster, more efficient in handling **overfitting**, and can process large datasets better than standard Gradient Boosting.
- **Advantages**: Fast, better at handling overfitting.  
- **Disadvantages**: Requires complex parameter tuning.  

### **Improvement Process (Hyperparameter Tuning) with Grid Search**
GridSearchCV is a hyperparameter tuning method that searches for the best parameters using grid search with cross-validation.
The parameters tested for each model in GridSearchCV:
- **KNN**: `n_neighbors` and `weights`.  
- **RF, GB, XGBoost**: `n_estimators`, `max_depth`, and `learning_rate`.  

| Index | Model             | Best Score | Best Params                                                 |
|-------|-------------------|------------|-------------------------------------------------------------|
| 0     | KNN               | 0.8811      | {'n_neighbors': 5, 'weights': 'distance'}                   |
| 1     | Random Forest     | 0.8710      | {'max_depth': 32, 'n_estimators': 100, 'random_state': 42}  |
| 2     | Gradient Boosting | 0.8455      | {'learning_rate': 0.1, 'max_depth': 7, 'n_estimators': 150} |
| 3     | XGBoost           | 0.8568      | {'learning_rate': 0.1, 'max_depth': 7, 'n_estimators': 150} |

Based on experiments using GridSearchCV:  
1. KNN achieved the highest score (**0.8811**) with **n_neighbors = 5** and **weights = 'distance'**, indicating that KNN with distance-based weighting performs best in this scenario.  
2. Random Forest obtained a score of **0.871**, with **max_depth = 32**, **n_estimators = 100**, and **random_state = 42**, showing that the model remains strong with a sufficiently large tree depth and an optimal number of estimators.  
3. Gradient Boosting scored **0.8455**, with **learning_rate = 0.1**, **max_depth = 7**, and **n_estimators = 150**, indicating that while this model performs well, it falls behind KNN and Random Forest.  
4. XGBoost achieved a score of **0.8568**, with **learning_rate = 0.1**, **max_depth = 7**, and **n_estimators = 150**, performing slightly better than Gradient Boosting.  

---

## Evaluation

### **1. Mean Squared Error (MSE)**
MSE is an evaluation metric that measures the average squared difference between actual values (**y_true**) and predicted values (**y_pred**).  
**MSE Formula:**  

![MSE](https://github.com/user-attachments/assets/130f0de2-064a-4863-b6d8-687cbe63c645)

- **Lower MSE = better performance**  
- **Sensitive to outliers** since the error is squared.  

### **2. R-Squared (R²)**
R² measures how well a model explains the variance in the data.  
**R² Formula:**  

![R2](https://github.com/user-attachments/assets/e5f86371-c897-4647-a327-1896f573a9ac)

where:

![image](https://github.com/user-attachments/assets/3a3d44e1-d2d4-4339-a328-ee11c4a28e6b)

**R² Interpretation:**  
- **\( R² = 1 \)** → Perfect model.  
- **\( R² = 0 \)** → Model is no better than the mean.  
- **\( R² < 0 \)** → Model performs worse than a random guess.  

### **Model Evaluation Results**

#### Model Performance Comparison

| Index | Model             | MSE                   | R²                  |
|-------|-------------------|-----------------------|----------------------|
| 0     | KNN               | 0.0188                | 0.8836               |
| 1     | Random Forest     | 0.0198                | 0.8773               |
| 2     | Gradient Boosting | 0.0237                | 0.8534               |
| 3     | XGBoost           | 0.0212                | 0.8692               |

#### Mean Squared Error (MSE) Comparison

| Model              | Train MSE              | Test MSE               |
|--------------------|-----------------------|------------------------|
| KNN               | 0.0000                 | 0.0188                 |
| Random Forest     | 0.0026                 | 0.0198                 |
| Gradient Boosting | 0.0107                 | 0.0237                 |
| XGBoost           | 0.0124                 | 0.0212                 |

![image](https://github.com/user-attachments/assets/e2f3a044-32d6-4dd1-8d42-db2506015dd5)

### **Model Performance Analysis**  

#### **Model Comparison**  

- **KNN** achieved the best performance with **MSE of 0.0188** and **R² of 0.8836**, indicating the smallest prediction error and the best predictive capability.  
- **Random Forest** had an **MSE of 0.0198** and **R² of 0.8773**, slightly lower than KNN but still demonstrating solid performance.  
- **XGBoost** recorded an **MSE of 0.0212** and **R² of 0.8692**, performing better than Gradient Boosting but still lower than KNN and Random Forest.  
- **Gradient Boosting** had an **MSE of 0.0237** and **R² of 0.8534**, showing higher prediction errors compared to the other models.  

#### **MSE Analysis on Training and Test Data**  

- **KNN had an MSE of 0.0 on training data**, indicating that the model memorized the training data completely. However, it still generalizes well to test data with an MSE of 0.0188.  
- **Random Forest showed a small difference between training MSE (0.0026) and test MSE (0.0198)**, indicating that it learned the data patterns well without overfitting.  
- **Gradient Boosting and XGBoost showed small differences between training and test MSE**, but their test MSE remains higher than KNN and Random Forest, indicating that while these models capture data patterns well, they do not generalize as optimally as KNN and Random Forest.  

### Prediction Results of the Four Models

| y_true | KNN Prediction | Random Forest Prediction | Gradient Boosting Prediction | XGBoost Prediction |
|--------|---------------|-------------------------|-----------------------------|--------------------|
| 17068  | 33.46        | 33.5                    | 33.5                        | 33.5              | 33.500000        |
| 19145  | 34.15        | 34.1                    | 34.1                        | 34.1              | 34.099998        |
| 2816   | 33.94        | 33.8                    | 33.9                        | 34.1              | 34.099998        |
| 738    | 33.60        | 33.5                    | 33.5                        | 33.7              | 33.599998        |
| 9832   | 33.59        | 33.6                    | 33.6                        | 33.6              | -                |

- **For the first data point (y_true = 33.46)**, all models provided predictions very close to the actual value, with KNN predicting 33.5 and the other models giving the same prediction of 33.5.  
- **For the second data point (y_true = 34.15)**, all models produced nearly identical results, predicting 34.1 across the board.  
- **For the third data point (y_true = 33.94)**, KNN predicted slightly lower (33.8), while Random Forest gave 33.9. Meanwhile, Gradient Boosting and XGBoost provided the highest predictions at 34.1.  
- **For the fourth data point (y_true = 33.60)**, KNN and Random Forest predicted 33.5, while Gradient Boosting gave a slightly higher value (33.7), and XGBoost was almost identical to the actual value (33.6).  
- **For the fifth data point (y_true = 33.59)**, all models produced highly accurate predictions, nearly identical to y_true at 33.6.  

Overall, all models demonstrated strong performance, with predictions closely matching the actual values, especially in cases where the difference between y_true and the predictions was minimal.

---

## Conclusion
This study successfully identified the key factors influencing seawater salinity, namely **CO₂ pressure in water, sensor water temperature, sea surface temperature, CO₂ fraction in water, and CO₂ concentration in water**, all of which showed a positive correlation with salinity. To enhance data quality, dimensionality reduction was performed using **PCA**, standardization with **StandardScaler**, and data splitting with a **90:10 ratio**. 

From the experimental results, **KNN** demonstrated the best performance with an **R² of 0.8836** and an **MSE of 0.0188**, followed by **Random Forest**, **XGBoost**, and **Gradient Boosting**. Each applied solution had a positive impact, such as **PCA reducing multicollinearity**, **standardization improving model stability**, and **GridSearchCV ensuring optimal model performance**. 

Thus, this study successfully achieved all its objectives and provided effective solutions for predicting seawater salinity.
