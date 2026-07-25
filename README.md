# Asthma-prediction
**1. Data Preprocessing**
Loaded the dataset (asthma_disease_dataset.csv) — 2392 rows, 29 columns
Checked for missing values and duplicate rows — none were found (clean dataset)
Dropped non-informative columns (PatientID, DoctorInCharge) as they were not useful for prediction
Corrected illogical data — rows where LungFunctionFEV1 > LungFunctionFVC (medically impossible, since FEV1 is always less than or equal to FVC) were swapped
Performed feature encoding:
Age was binned into categories (Teenager, Adult, Senior) and one-hot encoded
BMI was binned into categories (Underweight, Normal, Overweight, Obese) and one-hot encoded
Ethnicity and EducationLevel were one-hot encoded
Continuous features (PhysicalActivity, DietQuality, SleepQuality, PollutionExposure, PollenExposure, DustExposure, LungFunctionFEV1, LungFunctionFVC) were converted into binary (0/1) form using a median-based threshold
Applied the IQR method to detect outliers — since the dataset is synthetic, no outliers were found
**2. Statistical / Exploratory Data Analysis (EDA)**
Generated countplots to examine the relationship between each feature and the target variable (Diagnosis)
Created boxplots to visually confirm the absence of outliers
Examined the distribution of the target variable (Diagnosis) — the dataset was found to be heavily imbalanced (No Asthma: 2268 vs Asthma: 124)
**3. Handling Class Imbalance**
Applied SMOTE (Synthetic Minority Oversampling Technique) — only on the training data, to synthetically balance the minority class (Asthma)
The test data was kept in its original, imbalanced form, so that evaluation reflects a realistic scenario
**4. Model Training**
Trained two classification models:
Logistic Regression (with class_weight='balanced' and feature scaling)
Random Forest Classifier (with class_weight='balanced')
Both models were fitted on the SMOTE-balanced training data
**5. Model Evaluation**
Both models were evaluated using Accuracy, Precision, Recall, F1-score, and the Confusion Matrix
At the default threshold (0.5), both models performed poorly in detecting the minority class (Asthma), with a recall of 0 — reflecting the weak relationship between the features and the target in this dataset
The decision threshold was adjusted to 0.3, which improved recall:
Model	Accuracy	Recall (Asthma)	F1-score (Asthma)
Logistic Regression	0.89	0.12	0.10
Random Forest	0.87	0.04	0.03

**Conclusion**: Logistic Regression outperformed Random Forest, particularly in detecting the minority class (Asthma).

Agar chahen to main isko ek formal Word document (.docx) ya PDF mein bhi bana ke de sakti hoon, taake seedha submit kar sakein — bata dein.



