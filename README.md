# Customer Churn Prediction and Retention Strategy

## Overview
A machine learning project that analyses customer churn in a telecommunications dataset and explores how predictive analytics can support customer retention strategies.

## Dataset
- **Source:** IBM Telco Customer Churn public dataset
- **Records:** 7,043 customers
- **Original features:** 21 columns
- **Target variable:** `Churn` (`Yes` or `No`)

## Technologies Used
- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- SQLite and SQL
- Google Colab

## Project Workflow
1. Loaded and explored the customer churn dataset.
2. Cleaned the data and converted `TotalCharges` to a numeric data type.
3. Analysed churn patterns across contract types, tenure, monthly charges, internet services, and payment methods.
4. Prepared numerical and categorical features for machine learning.
5. Split the data into training and testing sets using an 80/20 stratified split.
6. Trained and evaluated Logistic Regression and Decision Tree classifiers.
7. Compared models using accuracy, precision, recall, F1-score, and confusion matrices.
8. Evaluated different probability thresholds to understand the trade-off between identifying churners and generating false alarms.
9. Used SQL queries to analyse churn distribution and churn rates by contract type and payment method.

## Exploratory Data Analysis: Findings

The analysis of the dataset found:

- Overall customer churn rate: **26.54%** (1,869 customers).
- Month-to-month contract churn rate: **42.71%**.
- One-year contract churn rate: **11.27%**.
- Two-year contract churn rate: **2.83%**.
- Electronic-check payment churn rate: **45.29%**.

These findings indicate associations in the dataset, not proof that a particular contract or payment method causes churn.

## Machine Learning Model Comparison

The models were evaluated on a held-out test set.

| Metric | Logistic Regression | Decision Tree |
|---|---:|---:|
| Accuracy | 80.55% | 73.95% |
| Precision (Churn) | 65.72% | 50.60% |
| Recall (Churn) | 55.88% | 79.14% |
| F1-score (Churn) | 60.40% | 61.73% |

### Interpretation
- Logistic Regression achieved higher accuracy and precision.
- The Decision Tree identified a larger proportion of actual churners, achieving higher recall, but also produced more false positives.
- The appropriate model depends on the business objective and the costs of missed churners versus unnecessary retention offers.

## Threshold Analysis

Different probability thresholds were compared to understand how classification decisions affect precision, recall, F1-score, and the number of customers flagged for retention.

On the validation analysis, a threshold of 0.3 achieved 89.0% recall, while a threshold of 0.5 achieved 77.9% recall. The lower threshold flagged more customers and had lower precision.

Threshold selection should consider retention campaign capacity, intervention costs, and the value of preventing customer churn.

## SQL Analysis

SQL queries using SQLite were used to:
- Calculate overall churn distribution.
- Calculate churn rates by contract type.
- Calculate churn rates by payment method.

The results highlighted month-to-month contracts and electronic-check payments as groups worth investigating for targeted retention strategies.

## Business Recommendations

1. **Investigate month-to-month churn:** Evaluate whether suitable longer-term plans, loyalty benefits, or retention offers could improve customer retention.
2. **Review electronic-check customers' experience:** Investigate whether payment friction, billing concerns, or other factors are associated with their higher observed churn.
3. **Use risk scores to prioritise outreach:** Test retention campaigns on appropriately selected high-risk customers and measure their effectiveness before wider deployment.

These recommendations are hypotheses for further investigation, not proven causal effects.

## Limitations
- The analysis uses a public dataset rather than live company customer data.
- Predictive performance on this dataset may not generalise to other telecom companies or future customers.
- Model evaluation metrics alone do not establish the financial value of a retention strategy.
- Threshold selection should be validated against business costs and campaign capacity.

## How to Run
1. Download or clone this repository.
2. Install the required packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Open `Customer_Churn_Prediction.ipynb` in Jupyter Notebook or Google Colab.
4. Upload the IBM Telco Customer Churn CSV dataset when prompted, or update the dataset path to match your local file.
5. Run the notebook cells in order.

## Project Status
Machine learning analysis, model comparison, threshold analysis, and SQL exploration have been implemented in the notebook. A standalone interactive application is not currently included.
