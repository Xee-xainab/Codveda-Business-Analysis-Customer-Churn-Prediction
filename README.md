# Customer Churn Prediction and Analysis

## Business Analytics Internship Project

This project analyzes customer churn patterns and develops a machine learning model to predict customers who are at risk of churning.

The analysis combines exploratory data analysis (EDA), customer behavior analysis, feature engineering, and Random Forest classification to identify important factors associated with customer churn and provide actionable recommendations for customer retention.

---

## Business Problem

Customer churn can reduce revenue and increase the cost of acquiring new customers. Understanding which customer characteristics, service plans, usage patterns, and service interactions are associated with churn can help businesses identify customers who may require retention attention.

This project addresses the following business questions:

- What proportion of customers have churned?
- Which customer characteristics and service plans are associated with higher churn rates?
- How do customer usage patterns differ between churned and non-churned customers?
- Does the frequency of customer service interactions differ between the two groups?
- Are there noticeable differences in churn rates across states?
- Which variables are most influential in predicting customer churn?
- How effectively can a machine learning model identify customers at risk of churn?

---

## Project Objectives

- Analyze customer churn patterns.
- Identify variables associated with customer churn.
- Compare customer behavior between churned and non-churned customers.
- Explore differences across service plans and geographic regions.
- Build a machine learning model for churn prediction.
- Evaluate model performance using multiple metrics.
- Provide actionable recommendations to support customer retention.

---

## Dataset

The project uses the **Churn 80 dataset (`churn-bigml-80.csv`)**.

| Attribute | Description |
|---|---|
| Records | 2,666 customers |
| Variables | 20 |
| Target Variable | Churn |
| Missing Values | None |
| Duplicate Records | None |
| Categorical Variables | State, International plan, Voice mail plan |
| Target Type | Binary classification |

The dataset contains customer account information, service-plan details, usage behavior, customer service interactions, and churn status.

---

## Tools and Technologies

- Python
- Jupyter Notebook
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Random Forest Classification

---

## Analytical Workflow

The project followed the following analytical process:

1. Data loading
2. Data understanding
3. Data quality checks
4. Exploratory data analysis
5. Feature engineering
6. Categorical variable encoding
7. Train-test splitting
8. Random Forest model development
9. Model prediction
10. Model evaluation
11. Feature importance analysis
12. Business insights
13. Retention recommendations

---

## Exploratory Data Analysis

### Overall Churn

The dataset contains:

- **2,666 customers**
- **388 churned customers**
- **2,278 non-churned customers**
- Overall churn rate: **14.6%**

This shows that churn is the minority class in the dataset, making it important to evaluate the model using metrics beyond accuracy.

---

### International Plan and Churn

Customers with an international plan had a churn rate of **43.70%**, compared with **11.27%** among customers without an international plan.

**Why it matters:**  
International-plan customers represent a group with a substantially different observed churn rate and should be investigated further when designing retention strategies.

---

### Voice Mail Plan and Churn

Customers with a voice mail plan had an observed churn rate of **8.87%**, compared with **16.71%** among customers without the plan.

**Why it matters:**  
The difference suggests that voice mail plan status may contain useful information for understanding customer churn patterns. However, the analysis does not establish that the plan itself causes lower churn.

---

### Daytime Usage and Churn

Average total daytime usage was:

- **Non-churned customers:** 175.10 minutes
- **Churned customers:** 205.18 minutes

Churned customers therefore recorded approximately **30 additional daytime minutes on average**.

**Why it matters:**  
Daytime usage showed one of the clearest differences between churned and non-churned customers and was also the most influential feature in the Random Forest model.

---

### Customer Service Calls and Churn

Average customer service calls were:

- **Non-churned customers:** 1.45
- **Churned customers:** 2.21

Churned customers averaged approximately **0.75 more customer service calls**.

**Why it matters:**  
Frequent customer service interactions may help identify customers who require additional attention, making this variable useful for churn monitoring and retention analysis.

---

### International Calls and Churn

Average international calls were:

- **Non-churned customers:** 4.54
- **Churned customers:** 4.05

The difference was relatively small compared with other variables examined.

**Why it matters:**  
International call frequency alone showed a limited difference between the two groups and should therefore be considered alongside other customer characteristics rather than used as a standalone churn indicator.

---

### Geographic Churn Patterns

The states with the highest observed churn rates among the top results were:

| State | Churn Rate |
|---|---:|
| TX | 29.09% |
| NJ | 28.00% |
| AR | 23.40% |
| MD | 23.33% |
| MS | 22.92% |
| SC | 22.45% |
| ME | 22.45% |
| MI | 22.41% |
| PA | 22.22% |
| NV | 21.31% |

**Why it matters:**  
Churn rates varied across states, suggesting that geographic patterns may provide additional context for customer retention analysis.

---

# Machine Learning Model

## Model Used

A **Random Forest Classifier** was developed to predict customer churn.

The model was configured with:

- **100 decision trees**
- `random_state = 42`

Categorical variables were converted into numerical values before modelling, and the `State` variable was one-hot encoded.

After feature engineering, the dataset contained **68 model features**.

---

## Train-Test Split

The dataset was divided into:

- **80% training data:** 2,132 customers
- **20% testing data:** 534 customers

Stratified splitting was used to maintain the churn class distribution across the training and testing datasets.

---

# Model Performance

The Random Forest model achieved the following results on the test dataset:

| Metric | Result |
|---|---:|
| Accuracy | **94.38%** |
| ROC-AUC | **0.89** |
| Churn Precision | **1.00** |
| Churn Recall | **0.62** |
| Churn F1-Score | **0.76** |

### Confusion Matrix

| | Predicted Not Churn | Predicted Churn |
|---|---:|---:|
| Actual Not Churn | 456 | 0 |
| Actual Churn | 30 | 48 |

The model correctly identified **48 of the 78 actual churners** in the test set, while **30 churners were not identified**.

The model produced **zero false positives** in this test set.

---

## Feature Importance

The most influential variables in the Random Forest model included:

1. **Total day minutes**
2. **Total day charge**
3. **Customer service calls**
4. **International plan**
5. Other customer usage and service-related variables

Customer service calls had an importance value of approximately **0.108**.

**Why it matters:**  
The model indicates that customer usage intensity and service interactions contain useful information for distinguishing churn outcomes.

---

# Key Business Insights

### 1. Churn affects 14.6% of customers

The dataset contains 388 churned customers out of 2,666.

**Business implication:**  
Customer churn represents a measurable retention issue that can be monitored using customer-level data.

### 2. International-plan customers show a higher observed churn rate

The churn rate was 43.70% for customers with an international plan compared with 11.27% for customers without one.

**Business implication:**  
International-plan customers could be investigated more closely to understand their service experience, pricing, usage patterns, and retention needs.

### 3. Churned customers have higher daytime usage

Churned customers averaged 205.18 daytime minutes compared with 175.10 minutes among non-churned customers.

**Business implication:**  
High daytime usage can be included as one of the indicators considered when monitoring potential churn risk.

### 4. Churned customers make more customer service calls

Churned customers averaged 2.21 customer service calls compared with 1.45 among non-churned customers.

**Business implication:**  
Repeated service interactions may provide an opportunity to identify customers who need additional support or follow-up.

### 5. Churn patterns vary across states

Several states recorded churn rates above 20%.

**Business implication:**  
Regional patterns can be monitored to determine whether differences are associated with customer mix, service experience, usage behavior, or other business factors.

### 6. Machine learning can support churn-risk identification

The Random Forest model achieved 94.38% accuracy and a ROC-AUC of 0.89, while identifying 48 of the 78 actual churners in the test dataset.

**Business implication:**  
The model can support the prioritization of customers for retention analysis, but it should not be treated as the only basis for customer decisions because some actual churners were missed.

---

# Business Recommendations

### 1. Develop a Churn-Risk Monitoring Process

Use customer usage, service-plan, and service-interaction variables to create a structured process for monitoring potential churn risk.

### 2. Investigate International-Plan Customers

Review the experience of customers with international plans, including pricing, usage patterns, service interactions, and customer satisfaction indicators.

### 3. Monitor Frequent Customer Service Interactions

Flag customers with repeated customer service calls for further investigation and proactive support.

### 4. Review High-Usage Customers

Monitor customers with high daytime usage and assess whether their current plans adequately match their usage patterns.

### 5. Monitor Regional Churn Patterns

Track churn rates by state over time and investigate persistent regional differences before implementing region-specific interventions.

### 6. Evaluate Retention Outcomes

Measure churn before and after retention interventions to determine whether the actions are associated with improved customer retention.

### 7. Use the Model as a Decision-Support Tool

Use the Random Forest model to help prioritize customers for further review rather than using predictions as the sole basis for retention decisions.

---

# Conclusion

This project combined exploratory data analysis and machine learning to investigate customer churn.

The analysis identified differences in customer plans, usage behavior, service interactions, and geographic churn patterns between customers who churned and those who remained.

A Random Forest classification model was developed to combine these variables and predict customer churn. The model achieved 94.38% accuracy and a ROC-AUC of 0.89 on the test dataset.

The analysis identified Total day minutes, Total day charge, and Customer service calls among the most influential features in the model.

The findings can support a structured customer retention process by helping businesses identify patterns associated with churn and prioritize customers for further investigation and retention efforts.

# Author
**Zainab Danjuma**

## Data Analyst | Excel | SQL | Power BI | Python

## Skills Demonstrated
- Data Cleaning
- Exploratory Data Analysis
- Feature Engineering
- Data Visualization
- Statistical Analysis
- Machine Learning
- Classification
- Model Evaluation
- Business Analysis
- Customer Retention Analysis
