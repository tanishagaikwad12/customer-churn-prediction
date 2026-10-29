# Customer Churn Prediction and Retention Strategy

## Overview

A machine learning project that analyses customer churn in a telecommunications dataset and explores how predictive analytics can support customer retention strategies.

## Dataset

- **Source:** IBM Telco Customer Churn public dataset
- **Records:** 7,043 customers
- **Original features:** 21 columns
- **Target variable:** `Churn` (`Yes` or `No`)

The dataset is used for exploratory data analysis, predictive modelling, and identifying customer segments with different observed churn rates.

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
8. Evaluated different probability thresholds to understand the trade-off between identifying churners and generating false positives.
9. Used SQLite and SQL queries to analyse churn distribution and churn rates by contract type and payment method.

## Exploratory Data Analysis: Findings

The analysis identified the following patterns:

- **Overall churn rate:** 26.54% (1,869 customers).
- **Month-to-month contract churn rate:** 42.71%.
- **One-year contract churn rate:** 11.27%.
- **Two-year contract churn rate:** 2.83%.
- **Electronic-check payment churn rate:** 45.29%.
- **Fiber-optic internet churn rate:** 41.89%.

These findings indicate associations in the dataset. They do not prove that contract type, payment method, or internet service causes churn.

## Machine Learning Model Comparison

The models were evaluated on a held-out test set.

| Metric | Logistic Regression | Decision Tree |
|---|---:|---:|
| Accuracy | 80.55% | 73.95% |
| Precision (Churn) | 65.72% | 50.60% |
| Recall (Churn) | 55.88% | 79.14% |
| F1-score (Churn) | 60.40% | 61.73% |

### Interpretation

- **Logistic Regression** achieved higher accuracy and precision.
- **Decision Tree** identified a larger proportion of actual churners, achieving higher recall, but also generated more false positives.
- The appropriate model depends on the business objective and the relative costs of missed churners versus unnecessary retention offers.

Accuracy alone is not sufficient for evaluating churn prediction because the dataset contains more customers who stayed than customers who churned.

## Threshold Analysis

Different probability thresholds were compared using validation analysis to understand their effects on precision, recall, F1-score, and the number of customers flagged for retention.

| Threshold | Precision | Recall | F1-score | Customers Flagged |
|---|---:|---:|---:|---:|
| 0.3 | 41.4% | 89.0% | 56.5% | 643 |
| 0.4 | 46.2% | 86.3% | 60.1% | 559 |
| 0.5 | 51.4% | 77.9% | 62.0% | 453 |
| 0.6 | 52.3% | 71.6% | 60.5% | 409 |
| 0.7 | 61.5% | 46.5% | 53.0% | 226 |

A lower threshold identifies more potential churners but flags more customers who may not churn. A higher threshold reduces the number of customers flagged but can miss more actual churners.

Threshold selection should consider retention campaign capacity, intervention costs, and the value of preventing customer churn. The best threshold cannot be determined from predictive metrics alone.

*Note: These are validation-analysis results, not the held-out test-set metrics reported in the model comparison.*

## SQL Analysis

SQL queries using an in-memory SQLite database were used to analyse customer churn.

The analysis covered:

- Overall churn distribution.
- Churn rates by contract type.
- Churn rates by payment method.

### Churn by Contract Type

| Contract Type | Total Customers | Churned Customers | Churn Rate |
|---|---:|---:|---:|
| Month-to-month | 3,875 | 1,655 | 42.71% |
| One year | 1,473 | 166 | 11.27% |
| Two year | 1,695 | 48 | 2.83% |

### Churn by Payment Method

| Payment Method | Total Customers | Churned Customers | Churn Rate |
|---|---:|---:|---:|
| Electronic check | 2,365 | 1,071 | 45.29% |
| Mailed check | 1,612 | 308 | 19.11% |
| Bank transfer (automatic) | 1,544 | 258 | 16.71% |
| Credit card (automatic) | 1,522 | 232 | 15.24% |

The results highlight customer segments worth investigating for targeted retention strategies. The observed differences do not establish causal relationships.

## Business Recommendations

1. **Investigate month-to-month churn:** Evaluate whether suitable longer-term plans, loyalty benefits, or retention offers could improve customer retention.
2. **Review electronic-check customers' experience:** Investigate whether payment friction, billing concerns, or other factors are associated with their higher observed churn.
3. **Use risk scores to prioritise outreach:** Test retention campaigns on appropriately selected high-risk customers and measure their effectiveness before wider deployment.
4. **Balance campaign reach and precision:** Choose a prediction threshold based on campaign capacity, intervention costs, and the consequences of missing potential churners.

These recommendations are hypotheses for further investigation, not proven causal effects or demonstrated financial outcomes.

## Limitations

- The analysis uses a public dataset rather than live company customer data.
- Predictive performance on this dataset may not generalise to other telecommunications companies or future customers.
- Model evaluation metrics alone do not establish the financial value of a retention strategy.
- Threshold selection should be validated against business costs and campaign capacity.
- A standalone interactive application is not currently included.

## How to Run

1. Clone or download this repository.
2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Open `Customer_Churn_Prediction.ipynb` in Google Colab or Jupyter Notebook.
4. Obtain the IBM Telco Customer Churn CSV dataset from its public source.
5. Upload the CSV to the notebook environment or update the dataset-loading cell to use the correct local file path.
6. Run the notebook cells in order.

The notebook uses an in-memory SQLite database for SQL analysis, so a separate database server is not required.

## Project Status

The project includes data cleaning, exploratory data analysis, machine learning model comparison, threshold analysis, SQL exploration, and business recommendations.

A standalone interactive application is not currently included.