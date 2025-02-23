# SyriaTel Customer Churn Prediction

## Overview
This project aims to predict customer churn for SyriaTel, a telecommunications company. By leveraging machine learning, SyriaTel can proactively identify at-risk customers and implement retention strategies to reduce churn and improve customer satisfaction.

## Business Problem
Customer churn is a significant issue in the telecommunications industry, leading to revenue loss and increased customer acquisition costs. SyriaTel, a major telecom provider, faces challenges in retaining customers due to factors such as service dissatisfaction, pricing competition, and evolving customer needs. Understanding why customers leave and predicting churn can help SyriaTel implement targeted retention strategies, improve customer satisfaction, and maintain market competitiveness.

## Main Objective
To develop a predictive model that accurately identifies customers likely to churn from SyriaTel, enabling the company to take proactive measures to retain high-risk customers.

### Specific Objectives
- To analyze customer data and identify key features that influence churn, providing insights into customer behavior and potential business strategies.
- To build, evaluate, and compare multiple classification models, ensuring the selection of the most effective model for predicting churn.
- To optimize model performance through hyperparameter tuning and threshold adjustment, improving the balance between precision and recall.
- To provide actionable recommendations based on model results, helping SyriaTel implement data-driven strategies to reduce churn and improve customer loyalty.

## Business and Data Understanding
### Business Context
Customer churn is a significant challenge in the telecommunications industry, leading to revenue loss and increased acquisition costs. SyriaTel is experiencing a decline in its customer base and wants to identify customers likely to leave before they churn. By predicting churn, the company can take targeted actions such as offering discounts, improving customer service, and personalizing engagement strategies.

### Dataset
The dataset used in this project is the SyriaTel Customer Churn Dataset (`bigml_59c28831336c6604c800002a.csv`). It contains approximately 3,333 rows and 21 columns.
The dataset includes various customer attributes such as call minutes, service usage, contract type, and customer service interactions. The target variable is churn, indicating whether a customer left the service (1) or remained (0).

In addition to existing features, I created three new aggregated features—**Total Minutes, Total Calls, and Total Charges**—to capture overall customer usage patterns. These features help in understanding how total usage contributes to churn.

## Data Analysis
### Univariate Analysis
- **Distribution of Total Day Minutes**
- **Distribution of Churn**

### Bivariate Analysis
- **Churn Distribution by Categorical Features**
- **Numerical Features vs. Churn**

### Multivariate Analysis
- **Feature Analysis Pairplot**
- **Correlation Heatmap**

## Data Processing and Model Selection
### Data Processing
- **Exploratory Data Analysis (EDA):** Performed initial data exploration to understand feature distributions, correlations, and missing values.
- **Feature Selection:** Based on the EDA, we selected 20 relevant features by removing redundant and low-impact variables.
- **Data Cleaning:** Null values were handled, and categorical variables were encoded for model compatibility.
- **Data Balancing:** Since the dataset was imbalanced (fewer churn cases), I applied **SMOTE (Synthetic Minority Over-sampling Technique)** to balance the classes and improve model performance.
- **Cleaned Data:** After completing data processing, I saved the data as `cleaned_telecom_data`.

## Modeling
### Step-by-Step Model Development
1. **Logistic Regression (Baseline Model)**
   - Baseline model with poor recall for churned customers.
   - Even after tuning the decision threshold, results remained unsatisfactory.
2. **Decision Tree Model**
   - Slightly better recall but still imbalanced.
   - Tuning improved performance but resulted in many false positives.
3. **Random Forest (Tuned)**
   - Significant improvement in both recall and precision.
   - Performed well but was tested against another model for comparison.
4. **XGBoost (Final Model - Tuned)**
   - Outperformed all previous models after hyperparameter tuning.
   - Provided the best balance of precision, recall, and overall accuracy.

## Final Model: Tuned XGBoost
After rigorous testing, we selected **XGBoost** as the final model due to its superior performance. The classification report is as follows:

```
               precision    recall  f1-score   support

       False       0.97      0.96      0.97       566
        True       0.79      0.86      0.82       101

    accuracy                           0.94       667
   macro avg       0.88      0.91      0.90       667
weighted avg       0.95      0.94      0.95       667
```

- **Accuracy:** **94%**  
- **F1-score:** **82%** for churn class  
- **Recall:** **86%** for churn class  
- **Precision:** **79%** for churn class  

### Confusion Matrix
| Actual \ Predicted | No Churn | Churn |
|-------------------|---------|------|
| No Churn         | 552     | 14   |
| Churn            | 14      | 87   |

## Feature Importance
- **Customer Service Calls** → Frequent complaints signal dissatisfaction.
- **Total Charges** → Higher billing correlates with churn risk.
- **International Plan** → Expensive plans contribute to customer loss.
- **Voice Mail Plan** → Some plans may be underutilized.

## Recommendations
- **Enhance Customer Retention Strategies** → Identify high-risk customers based on churn indicators and offer personalized retention plans.
- **Improve Customer Service Quality** → Address frequent complaints by improving support efficiency and issue resolution.
- **Optimize Service and Pricing Plans** → Adjust international and voicemail plans to provide better value for customers.
- **Deploy Real-Time Churn Prediction** → Implement the XGBoost model in SyriaTel’s system for early intervention and customer retention efforts.

## Conclusion
The final **Tuned XGBoost model** provided the best balance between precision and recall, making it the most effective tool for churn prediction. By identifying key churn factors, SyriaTel can take proactive measures to retain customers and reduce churn-related revenue loss.

