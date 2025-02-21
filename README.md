# SyriaTel Customer Churn Prediction

## Overview
This project aims to predict customer churn for SyriaTel, a telecommunications company. Customer churn is a critical business problem as losing customers directly impacts revenue. By identifying customers who are likely to churn, SyriaTel can take proactive measures to retain them, such as offering personalized plans, discounts, or improved customer service.

The goal of this project is to build a classification model that predicts whether a customer will churn based on their usage patterns, demographics, and billing information.

## Business and Data Understanding

### Stakeholder
The primary stakeholder is SyriaTel, a telecommunications company interested in reducing customer churn.

### Business Problem
Customer churn is a significant issue in the telecom industry. SyriaTel wants to identify customers who are likely to stop using their services so they can take targeted retention actions. This project will help SyriaTel:

- Predict which customers are at risk of churning.
- Understand the key factors driving churn.
- Develop actionable strategies to retain customers.

### Dataset
The dataset used in this project is the SyriaTel Customer Churn Dataset from Kaggle. It contains approximately 3,333 rows and 21 columns, including:

- **Target Variable**: `churn` (binary: Yes/No)
- **Features**: Customer demographics (e.g., state, area code), call details (e.g., total day minutes, total evening calls), and billing information (e.g., total charges, account length)

## Data Processing and Model Selection

### Data Processing

- **Exploratory Data Analysis (EDA):** We performed initial data exploration to understand feature distributions, correlations, and missing values.
- **Feature Selection:** Based on the EDA, we selected 20 relevant features by removing redundant and low-impact variables.
- **Data Cleaning:** Null values were handled, and categorical variables were encoded for model compatibility.
- **Data Balancing:** Since the dataset was imbalanced (fewer churn cases), we applied **SMOTE (Synthetic Minority Over-sampling Technique)** to balance the classes and improve model performance.

### Model Selection and Optimization

- **Baseline Model:** We first implemented a **Logistic Regression model**, but it struggled with recall for the churn class.
- **Advanced Models:** We then tested **Random Forest**, which showed significantly better performance in recall and precision.
- **Threshold Tuning:** Instead of using the default 0.5 threshold, we optimized the decision threshold by analyzing precision-recall trade-offs to maximize the F1-score for the churn class.

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

## Conclusion

- The **Random Forest model** successfully identifies customers likely to churn with **high recall and precision**.
- The model achieves an **F1-score of 80%** for the churn class, ensuring a good balance between false positives and false negatives.
- The insights from this model can help SyriaTel **proactively engage at-risk customers**, reducing churn rates and improving customer retention strategies.

