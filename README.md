# Alzheimer-Prediction using ML 
# Introduction 
Alzheimer’s disease is a progressive neurodegenerative disorder that affects memory, thinking ability, and behavior. Early prediction of Alzheimer’s is crucial, as timely diagnosis can help individuals seek medical intervention and adopt treatment strategies that may slow disease progression. Machine learning offers the capability to identify subtle patterns in patient health data that may not be easily detectable by traditional diagnostic methods.

In this project, we aim to build a predictive system that classifies whether a patient is likely to have Alzheimer's disease based on lifestyle, medical history, and cognitive assessments. The objective is to evaluate several machine learning models and identify the approach that produces the most reliable predictive performance.

# Dataset Description
Dataset Source: [Alzheimer's Disease Dataset](https://www.kaggle.com/datasets/rabieelkharoua/alzheimers-disease-dataset) (Kaggle)

The dataset contains 2149 patient records and includes variables spanning demographics, lifestyle habits, cognitive symptoms, and medical conditions. The dataset consists of 35 features consists of Patient ID, Demographic Details, Lifestyle Factors, Medical History, Clinical Measurements, Cognitive and Functional Assessments, Symptoms, Diagnosis Information and some Confidential Information. 

# Data Preprocessing

**Removing Irrelevant Features**: PatientID and DoctorInCharge were dropped as they do not convey predictive information.

**Handling Data Types & Missing Values**: The dataset does not contain missing values, so no imputation was required.

**Encoding Categorical Variables**: Several features such as Gender, Ethnicity, and Medical Conditions were already in numerical form. Therefore, no encoding step was necessary.

**Feature Scaling**: Numerical features like Age, BMI, SleepQuality, etc., were standardized to improve model convergence and stability.

**Train-Test Split**: Data was split into 70% training and 30% testing to evaluate model generalization performance.

# Model Training and Evaluation

We treated this as a binary classification problem where the goal is to predict whether a patient has Alzheimer’s or not (Diagnosis: 0 or 1). 
**Models Used**: 

**Random Forest Classifier**: Random Forest performed very well, achieving 94.42% accuracy. This model works by building many decision trees during training and combining their outputs through majority voting. Because each tree learns slightly different patterns, the final result becomes more stable and robust. The high precision indicates that when the model predicts Alzheimer’s, it is usually correct; however, its slightly lower recall shows that it sometimes misses individuals who actually have the disease.

**Support Vector Machine (SVM)**: CatBoost achieved the highest performance overall, with 94.88% accuracy and the best balance between precision and recall. CatBoost is a gradient boosting algorithm that builds trees sequentially, where each new tree attempts to correct the errors of previous ones. It handles categorical and structured data effectively and automatically reduces overfitting. Its higher recall means it is better at identifying patients who truly have Alzheimer’s, making it a strong candidate for medical screening applications.

**CatBoost Classifier**: SVM with RBF kernel performed lower than the other two, achieving 83.49% accuracy. SVM tries to find the best separating boundary (hyperplane) between classes by transforming the data into a higher-dimensional space using the RBF kernel. While powerful for complex, non-linear patterns, SVM performance can drop when there are many features or when the classes overlap significantly. This is reflected in the lower recall and F1-score, meaning it struggled to consistently detect Alzheimer’s cases.
