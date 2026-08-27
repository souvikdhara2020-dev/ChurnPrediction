# Customer Churn Prediction

This project focuses on predicting customer churn using machine learning.

Customer churn prediction can help a telecommunication company identify customers who are more likely to leave the service. In this project, customer information such as tenure, services, contract type, payment method, monthly charges and total charges is used to build classification models.

## Project Objective

The main objective of this project is to:

- Explore and understand the customer churn dataset
- Clean and preprocess the data
- Perform feature engineering
- Build different machine learning classification models
- Compare the performance of the models
- Handle class imbalance
- Select a suitable model for customer churn prediction

## Dataset

The original dataset contains:

- 7,043 customer records
- 21 columns
- Customer demographic information
- Phone and internet service information
- Contract and payment information
- Monthly and total charges
- Churn information

The target variable is:

- `Churn` — whether the customer has left the service

The original dataset contains both numerical and categorical variables.

## Project Workflow

The project is divided into three main stages:

### 1. Exploratory Data Analysis

The EDA stage includes:

- Loading the dataset
- Understanding the shape and structure of the data
- Checking data types
- Checking missing values
- Examining numerical statistics
- Exploring customer and churn-related variables
- Visualizing the data

The `TotalCharges` column was initially stored as a string. It was converted into a numerical column during data cleaning.

After conversion, 11 missing values were found in `TotalCharges`. These records were removed because they represented a very small portion of the dataset.

### 2. Feature Engineering

Several new features were created to improve the representation of customer behaviour.

The following features were created:

- `TenureGroup`
- `AvgMonthlySpend`
- `NumAddOnServices`
- `HasInternet`

`customerID` was removed because it does not provide useful predictive information.

The target variable `Churn` was converted from:

- `Yes` → `1`
- `No` → `0`

### 3. Machine Learning

The data was divided into training and testing sets using an 80/20 split.

The training and testing sets were:

- Training: 5,625 records
- Testing: 1,407 records

The preprocessing pipeline handles numerical and categorical variables separately.

For numerical features:

- `StandardScaler` was used.

For categorical features:

- `OneHotEncoder` was used.

## Models Used

The following classification models were compared:

1. Logistic Regression
2. Random Forest
3. Gradient Boosting
4. XGBoost
5. LightGBM

The models were compared using stratified 5-fold cross-validation and ROC-AUC.

## Model Comparison

| Model | Mean ROC-AUC |
|---|---:|
| Logistic Regression | 0.8477 |
| Random Forest | 0.8438 |
| Gradient Boosting | 0.8481 |
| XGBoost | 0.8447 |
| LightGBM | 0.8368 |

Gradient Boosting achieved the highest mean ROC-AUC among the baseline models.

## Handling Class Imbalance

Customer churn datasets can contain an imbalance between customers who churn and customers who do not churn.

In this project, class imbalance was also addressed using SMOTEENN.

SMOTEENN combines oversampling with data cleaning to create a more balanced training dataset.

A Gradient Boosting classifier was trained using the resampled data.

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- XGBoost
- LightGBM
- Jupyter Notebook

## Project Structure

```text
Churn-Prediction-/
│
├── data/
│   ├── customer-churn-raw.csv
│   └── churn_cleaned.csv
│
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── Feature_Engeneering.ipynb
│   └── modelling.ipynb
│
├── models/
│   └── churn_model.pkl
│
└──  README.md
