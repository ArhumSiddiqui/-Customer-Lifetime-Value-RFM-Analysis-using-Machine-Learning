# CDNow-Customer-Lifetime-Value-Prediction

## Project Overview

This project involves the analysis of customer purchase data from the CDNow dataset to predict customer lifetime value (CLV) over a 90-day period. The analysis includes cohort analysis, temporal data splitting, feature engineering, and building machine learning models for both regression and classification tasks. The project utilizes the `PyCaret`, `XGBoost`, and various other machine learning and data manipulation libraries in Python.

## Dataset

The dataset is the **CDNow Customer Data**, which includes information on customer purchases such as:
- **customer_id**: Unique identifier for each customer.
- **date**: The date of purchase.
- **quantity**: The quantity of items purchased.
- **price**: The price of the items purchased.

The dataset contains 69,659 rows of transaction data spanning several months, and we use this data to analyze customer purchasing behavior and predict their future spending habits.

## Key Steps and Methods

### 1. Data Preparation
- The dataset was read from a CSV file and cleaned by:
  - Converting the `date` column to `datetime` format.
  - Dropping any rows with missing values.

### 2. Feature Engineering
- **Recency**: Days since the customer's most recent purchase before the cutoff date.
- **Frequency**: Number of transactions before the cutoff date.
- **Monetary Value**: Total and average amount spent by the customer before the cutoff.
  
  We created a cohort of customers and their purchase details to analyze behavior over time.

### 3. Temporal Splitting
- The dataset was split into:
  - **Training Data (Temporal In)**: Includes transactions before the 90-day cutoff period.
  - **Test Data (Temporal Out)**: Includes transactions within the last 90 days.

### 4. Targets
- **spend_90_total**: Total spend by the customer in the next 90 days.
- **spend_90_flag**: Binary label indicating whether the customer made any purchase in the next 90 days.

### 5. Machine Learning Models
We employed two machine learning tasks:

#### Regression (Predicting Spend Value)
- **Model**: XGBoost Regressor.
- **Target**: Predicting the total spending (`spend_90_total`) in the next 90 days.
- **Performance Metrics**: MAE, MSE, RMSE, and R².

#### Classification (Predicting Whether a Purchase Will Happen)
- **Model**: XGBoost Classifier.
- **Target**: Predicting if a customer will make a purchase in the next 90 days (`spend_90_flag`).
- **Performance Metrics**: Accuracy, AUC, Recall, Precision, F1-score.

### 6. Model Interpretation
- Feature importance was interpreted using model interpretability tools to understand which features were most influential in predicting customer spending behavior.
  
### 7. Business Insights
**Key Business Insights**:
- **Increasing 90-day Sales Value**: The model identified top customers with high predicted spending in the next 90 days. These customers can be targeted to increase sales value by personalized marketing strategies.
- **Increasing 90-day Purchase Probability**: Customers with recent purchases but low predicted spending probability can be re-engaged to ensure continuous buying patterns.
- **Missed Opportunities**: Some high-spend customers are no longer purchasing. Re-engagement campaigns can focus on these high-value customers.

## Results

The regression and classification models both yielded useful insights:

- **Regression Model**: Provides a ranked list of customers likely to spend the most in the next 90 days.
- **Classification Model**: Predicts the probability of customers making a purchase within 90 days, identifying those likely to buy soon.

The models enable businesses to focus marketing efforts on top spenders and re-engage customers with high spending potential.

## Conclusion

This project successfully demonstrates how to build predictive models for customer lifetime value based on historical purchase data. These insights help businesses optimize their marketing efforts by focusing on the most valuable customers.

## Dependencies

The following Python libraries were used:

```bash
pandas
numpy
seaborn
matplotlib
joblib
pycaret
xgboost
sklearn




