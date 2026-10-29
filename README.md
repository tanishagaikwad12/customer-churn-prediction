# Customer Churn Prediction and Retention Strategy

## Overview
A machine learning project that analyzes customer churn in a telecommunications dataset and explores how predictions can support customer-retention strategies.

## Dataset
- Public IBM Telco Customer Churn dataset
- 7,043 customer records
- 21 original columns
- Target variable: `Churn` (`Yes` or `No`)

## Technologies
- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- Google Colab

## Workflow
1. Loaded and cleaned the dataset.
2. Explored churn patterns by tenure, monthly charges, contract type, internet service, and payment method.
3. Prepared numerical and categorical features using imputation, scaling, and one-hot encoding.
4. Split the dataset into training and testing sets using an 80/20 stratified split.
5. Trained Logistic Regression and Decision Tree models.
6. Evaluated models using accuracy, precision, recall, F1-score, and confusion matrices.
7. Generated a high-risk customer list and developed retention recommendations.

## Model Results

| Metric | Logistic Regression | Decision Tree |
|---|---:|---:|
| Accuracy | 80.55% | 73.95% |
| Churn precision | 65.72% | 50.60% |
| Churn recall | 55.88% | 79.14% |
| Churn F1-score | 60.40% | 61.73% |

## Key Findings
- Month-to-month contract churn rate: 42.71%.
- One-year contract churn rate: 11.27%.
- Two-year contract churn rate: 2.83%.
- Fiber-optic customer churn rate: 41.89%.
- Electronic-check customer churn rate: 45.29%.

These are observed associations in the dataset and do not establish causation.

## Limitations
- Uses a public dataset rather than live business data.
- Evaluation uses a single train/test split.
- Predictions are estimates, not guarantees.
- Retention recommendations require further validation before real-world use.

## How to Run
1. Open `Customer_Churn_Prediction.ipynb` in Google Colab.
2. Upload the dataset CSV.
3. Confirm the CSV path in the loading cell.
4. Run the notebook cells in order.

## Project Type
Personal machine learning and business analytics project using a public dataset.