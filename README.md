# 📈 Predictive Health Analytics: Optimized Machine Learning Classifier for Diabetes Risk Assessment (PIMA Indian Cohort)
<img width="2752" height="1536" alt="image" src="https://github.com/user-attachments/assets/e37cb35b-e4ec-4630-984b-d4e2325d46bf" />

## 1. Data Context and Preparation

The project utilized the PIMA Indian Diabetes Dataset (PIDD), sourced from Mendeley Data, originally collected by the National Institute of Diabetes and Digestive and Kidney Diseases (NIDDK). The cohort consists of 768 Pima Indian females, aged 21 years or above.

*Feature Engineering and Preprocessing*:

• Inconsistent Data Handling: Several features, including Glucose, Blood Pressure, Skin Thickness, and Insulin, contained inconsistent '0' values. Since the distributions of most predictors were skewed, these 0 values were imputed using the median rather than the mean, which minimized the potential influence of outliers or extreme values.

• Data Splitting and Scaling: The data was split using a 90:10 training-testing ratio, which produced the best F1-Score and ROC-AUC Score. The splitting process was stratified by the outcome variable to preserve the intrinsic class imbalance in both sets. The features were then scaled using the Standard Scaler to manage their skewed distributions.

## 2. Model Selection and Optimization Pipeline
The objective was to develop a model that could accurately classify a person's risk of diabetes (binary classification: 0 = non-diabetic, 1 = diabetic).

Initial Screening and Metric Justification:

We initially evaluated six classification algorithms: Logistic Regression, KNN, Naïve Bayes, Decision Tree, Random Forest Classifier, and XGBoost Classifier.

• The evaluation prioritized the F1-Score and ROC-AUC Score. **The F1-Score was chosen because, in a medical diagnostic context, the costs associated with a false negative (missing a diagnosis) are high, requiring a metric that effectively balances precision and recall.**

• Logistic Regression, Random Forest, and Naïve Bayes were shortlisted based on their superior initial F1 and ROC-AUC performance metrics.

*Hyperparameter Tuning:*

The shortlisted models were optimized using the RandomizedSearchCV technique. This optimization led to the selection of the Random Forest Classifier as the final model due to its performance on the test set:

|Model                       | Final Accuracy     |Final F1 Score    |Final ROC AUC Score|
-----------------------      |------------------  |----------------  |-------------------|
|Random Forest               |     0.77           |     0.71         |      0.87         |
|Logistic Regression         |     0.73           |     0.64         |      0.83         |
|Naïve Bayes                 |     0.73           |     0.63         |      0.77         |

## 4. Feature Importance and Insights

The Random Forest model enables the extraction of Feature Importance Scores, translating predictive power into clinical utility. This provides critical information for targeted interventions and policy development.
The most significant predictors, ranked by importance, are:

1. Glucose
 
2. Body mass index (BMI)
 
3. Age
 
4. Insulin
