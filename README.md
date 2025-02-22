# SyriaTel Customer Churn Prediction

## Overview
This project aims to predict customer churn for SyriaTel, a telecommunications company. By leveraging machine learning, SyriaTel can proactively identify at-risk customers and implement retention strategies to reduce churn and improve customer satisfaction.

### Business Problem
Customer churn is a significant issue in the telecommunications industry, leading to revenue loss and increased customer acquisition costs. SyriaTel, a major telecom provider, faces challenges in retaining customers due to factors such as service dissatisfaction, pricing competition, and evolving customer needs. Understanding why customers leave and predicting churn can help SyriaTel implement targeted retention strategies, improve customer satisfaction, and maintain market competitiveness.

1. **Main Objective:**
   - To develop a predictive model that accurately identifies customers likely to churn from SyriaTel, enabling the company to take proactive measures to retain high-risk customers.

2. **Specific Objectives:**
   - To analyze customer data and identify key features that influence churn, providing insights into customer behavior and potential business strategies.
   - To build, evaluate, and compare multiple classification models, ensuring the selection of the most effective model for predicting churn.
   - To optimize model performance through hyperparameter tuning and threshold adjustment, improving the balance between precision and recall.
   - To provide actionable recommendations based on model results, helping SyriaTel implement data-driven strategies to reduce churn and improve customer loyalty.

## Business and Data Understanding

### Business Context
Customer churn is a significant challenge in the telecommunications industry, leading to revenue loss and increased acquisition costs. SyriaTel is experiencing a decline in its customer base and wants to identify customers likely to leave before they churn. By predicting churn, the company can take targeted actions such as offering discounts, improving customer service, and personalizing engagement strategies.

### Dataset
The dataset used in this project is the SyriaTel Customer Churn Dataset ("bigml_59c28831336c6604c800002a.csv"). It contains approximately 3,333 rows and 21 columns.
The dataset includes various customer attributes such as call minutes, service usage, contract type, and customer service interactions. The target variable is churn, indicating whether a customer left the service (1) or remained (0).

## Data Processing and Model Selection

### Data Processing
- **Exploratory Data Analysis (EDA):** Performed initial data exploration to understand feature distributions, correlations, and missing values.
- **Feature Selection:** Based on the EDA, we selected 20 relevant features by removing redundant and low-impact variables.
- **Data Cleaning:** Null values were handled, and categorical variables were encoded for model compatibility.
- **Data Balancing:** Since the dataset was imbalanced (fewer churn cases), I applied **SMOTE (Synthetic Minority Over-sampling Technique)** to balance the classes and improve model performance.

## Modeling
- **Baseline Model:** Implemented a **Logistic Regression model**, but it struggled with recall for the churn class.
- **Advanced Models:** Tested **Random Forest**, which showed significantly better performance in recall and precision.
- **Threshold Tuning:** Instead of using the default 0.5 threshold, I optimized the decision threshold by analyzing precision-recall trade-offs to maximize the F1-score for the churn class.

## Final Model: Random Forest Classifier

After rigorous testing, we selected **Random Forest** as the final model due to its superior performance. The classification report is as follows:

```
               precision    recall  f1-score   support

       False       0.98      0.94      0.96       566
        True       0.73      0.87      0.80       101

    accuracy                           0.93       667
   macro avg       0.85      0.91      0.88       667
weighted avg       0.94      0.93      0.93       667
```

- **Accuracy:** 93%
- **F1-score:** 80% for churn class
- **Recall:** 87% for churn class
- **Precision:** 73% for churn class

### Confusion Matrix

The confusion matrix shows that the model correctly predicts a significant portion of both churn and non-churn cases while maintaining a balanced trade-off between precision and recall.

| Actual \ Predicted | No Churn | Churn |
|-------------------|---------|------|
| **No Churn**     | 534     | 32   |
| **Churn**        | 13      | 88   |

## Recommendations
- SyriaTel should target high-risk customers with personalized retention offers to reduce churn rates.
- Customer support quality should be improved by reducing wait times and enhancing service training.
- Flexible pricing plans and contract incentives should be introduced to encourage long-term commitments.
- Customer usage patterns should be monitored to offer proactive service recommendations.
- A real-time churn monitoring system should be deployed to take immediate action on high-risk customers.

## Conclusion
The final model effectively predicts customer churn, identifying at-risk customers before they leave. By focusing on key churn drivers, SyriaTel can implement targeted retention strategies, such as personalized offers and improved customer support.
