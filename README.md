# Predicting Diabetes Risk: Phase3_Project

![diabetes_cover](https://github.com/ldwilker10/phase3_final_project/blob/main/phase3_final_project_draft/images/diabetes_cover.png)


#### Project by: Lucas Wilkerson
#### Date: 

## Project Overview

For this project I sought to develop a predictive model to identify individuals who are at higher risk of developing diabetes or have diabetes based on an array of health-related characteristics. Using this data and predictive models, health-care practitioners can improve patient outcomes by improving early diagnosis/ detection and preemptively implementing personalized treatment strategies for treatment and prevention of diabetes. 

## Business Problem/Stakeholder

A healthcare practice group is looking to improve diabetes diagnosis, improve prognosis of those who are diagnosed and assist patients looking to prevent diabetes. Utilizing this data, providers will be able to look for early detection signs of diabetes and then implement corrective strategies early on in the diesease process to either improve the patients outcome and health with the disease or prevent it altogether. Utilizing my model, the goal is to assist practitioners with early detection by building a predictive model that can identify individuals who have diabetes based health-related attributes such as blood pressure, glucose levels, insulin levels, BMI, age and other factors. 


## Data Understanding 

For my analysis, I utilized the below dataset that is provided on the website Kaggle. 
- diabetes.csv [https://www.kaggle.com/datasets/pkdarabi/diabetes-dataset-with-18-features/data] 

After cleaning and preparation, the final dataset contained 3260 rows with 18 columns containing numerical data types. The target variable is the presence of diabetes which is indicated by the "Diabetes" column. The independent, or feature, variables contain various health and lifestyle indicators ranging from numerical columns containing lab values of various health markers to categorical columns, such as smoking, drinking, and gender. Below is a list of the columns of the dataset. 

Columns of dataset:
- Age
- Gender
- BMI
- SBP (Systolic Blood Pressure)
- DBP (Diastolic Blood Pressure)
- FPG (Fasting Plasma Glucose)
- Cholesterol
- Triglyceride
- HDL (High-Density Lipoprotein)
- LDL (Low-Density Lipoprotein)
- ALT (Alanine Aminotransferase)
- BUN (Blood urea nitrogen)
- CCR (Creatinine Clearance)
- FFPG (Final Fasting Plasma Glucose)
- Smoking Status
- Drinking Status
- Family History
- Diabetes: presence of Diabetes

With the cleaned dataset, there are 3260 rows and in the context of the target variable count, 3000 are labeled as not having diabetes and 260 being labeled as having diabetes. 


![diabetes_count](https://github.com/ldwilker10/phase3_final_project/blob/main/phase3_final_project_draft/images/diabetes_count.png)


## Modeling 

Baseline Model: The initial baseline model was a simple logistic regression model with no hyperparameters tuned. SMOTE was applied to initial training data to account for the class imbalance in the dataset. 

- Train Score: 0.8984895601954687
- Test Score: 0.9030674846625767
- Cross Validation Scores: 0.86792453, 0.90344062, 0.89777778, 0.89777778, 0.90555556
- Accuracy Score: 0.9030674846625767
- Precision Score: 0.44715447154471544
- F1 Score: 0.5820105820105821
- Recall Score: 0.8333333333333334


Random Forest Classifier Model: A simple random forest classifier model with no hyperparameters tuned was also utilized.

- Train Score: 1.0
- Test Score: 0.9239263803680982
- Cross Validation Scores: 0.94339623, 0.96337403, 0.95888889, 0.96222222, 0.96555556
- Accuracy Score: 0.9239263803680982
- Precision Score: 0.5256410256410257
- F1 Score: 0.5694444444444445
- Recall Score: 0.6212121212121212


Other models that were tested included a simple Decision Tree Classifier Model and a simple K-Nearest Neighbors Model. These were not pursued after initial simple models due underperforming when compared to the Baseline Model and the Random Forest Classifier Model. 


## Best Model Results 

After tuning both the baseline model and random forest classifier model, and comparing all four models (baseline logistic, tuned logistic, rfc, tuned rfc), the tuned baseline logistic regression model had the best performance based our specific metrics of focus (F1 and Recall scores).

With the tuned baseline model, the scores were: 

- Train Score: 0.8978231896934695
- Test Score: 0.9042944785276074
- Cross Validation Scores: 0.86792453, 0.90566038, 0.90222222, 0.90111111, 0.90333333
- Accuracy (same as test) Score: 0.9042944785276074
- Precision Score: 0.45081967213114754
- F1 Score: 0.5851063829787234
- Recall Score: 0.8333333333333334


Train and test scores were very close in value indicating that there was not any signs of underfitting or overfitting with the model. While the test/accuracy score was not the best of all models, it's score of 0.904 is still adequate. Having a score of 0.904 indicates that out of all the predictions the model made, 90.3 % were correct. This includes true positives (individuals with diabetes) and true negatives(individuals without diabetes). 

Recall: The model's overall recall score was 0.833 which means that out of all of the individuals/patients that actually had diabetes, the model correctly identified 83.3 % of those. 

Precision: The model's overall precision score was 0.451 which indicates that out of all the times that the model stated that an individual had diabetes (predicted positives), 45.1 % of those actually had diabetes (true positives)

F1 Score: The model's overall score was 0.585 which takes into account both of precision and recall. Generally if this value is higher, this indicated the model is doing well all around. Having a value of 0.585 is lower than desired. Given that the model is skewed mored towards recall and less towards precision, the F1 score penalizes the model in this case. 

### Feature Importance for Best Model

![feature_importances_tuned_baseline](https://github.com/ldwilker10/phase3_final_project/blob/main/phase3_final_project_draft/images/feature_importances_tuned_baseline.png)

Most Important Features:

- FFPG (Final Fasting Plasma Glucose)
- Age
- FPG (Fasting Plasma Glucose)

When looking into the features, the most important features for this model are FFPG, Age and FPG with the most important feature being FFPG (Final Fasting Plasma Glucose). With these being the biggest predictors for the model (for identifying diabetes), these health metrics should be consistent monitored and considered by health care practitioners when reviewing health care plans.

![histogram_ffpg_dm_count](https://github.com/ldwilker10/phase3_final_project/blob/main/phase3_final_project_draft/images/histogram_ffpg_dm_count.png)


## Conclusion/ Recommendations 

The tuned baseline logistic regression model showed great performance in identifying those with diabetes based on the various features and health/lifestyles metrics. The model showed that out of all individuals with diabetes, it could correctly identify 83.3 % of those individuals. This can provide great benefit for healthcare practitioner's by increasing early detection and allowing for early treatment. By treating the disease early on, this can improve overall prognosis, improve patient outcomes by preventing accerleration of disease and negative health consequences while also decreasing the load on the healthcare system and the providers. 

Recommendations: 

- Healthcare providers should utilize this model as a tool for early diabetes detection/screen. While this model is not an official diagnostic tool for diabetes, this model can be useful for early detecton and screening. If an individual is flagged by the model, additional diagnostic testing can then be utilized to confirm disease status.

- Using this model, practitioner's can implement preventative health strategies to their patient population early on before disease progression. Such strategies or approaches could include dietary education or exercise recommendations. 

- In the context of identifying diabetes status and risk, healthcare practitioner's should focus on a patients FFPG, Age and FPG. 



## Limitations
While the model can be useful to predicting individuals with diabetes based on various health and lifestyles factors, the model is not perfect and does have it's limitations.

- False positives: When individuals actually have diabetes, the model correctly identifies those indiviudals approximiately 84.8% of the time. With having a higher recall, there is an increased risk of mislabeling indiviudals without diabetes as having diabetes. While there is this increased chance, having an increased risk if in correclty identifying someone as having diabetes is a better trade off in this situation that incorrectly labeling someone as not having diabetes when they in fact do have diabetes. If someone is labeled as a false positive, recommending increased care or lifestyle interventions to address diabetes may be more of an annoyance or inconvenience to a healthy patient, however this outcome would be better than if a patient with diabetes is not identified and is left untreated allowing the disease to progress and health to deteriorate.

- Low sample size (specifically individuals with diabetes): In the final dataset, patients with diabetes only accouted for roughly 7.98% of the sample. A larger sample could allow for better more thorough training of the model.

- Feature information: While most features were health markers that can be deciphered based on healthy guidelines, some features did not provide additional information on how they were valued/ measured making it difficult to understand their specific relationship to diabetes risk. 
 


## Repository Structure

├── Images    
├── Data   
├── .gitignore                                                                                                                   
├── [phase3_final_model.ipynb](add link to notebook)   
├── [diabetes_risk_prediction.pdf](add link to pdf)       
└── [README.md]( add link to readme)  