# Customer Churn and Segmentation Dashboard

This project is a Streamlit-based machine learning dashboard for analyzing telecom customer churn and grouping customers into useful business segments. It uses the Telco Customer Churn dataset to train a churn prediction model and a K-Means clustering model for customer segmentation.

## Project Overview

The application helps understand customer behavior through three main views:

- **Overview**: Shows business KPIs such as total customers, churn rate, average tenure, and average monthly charge.
- **Prediction**: Predicts whether a customer is likely to churn based on demographic, account, billing, and service details.
- **Segmentation**: Assigns a customer to a segment using tenure, monthly charges, total charges, and number of services used.

The churn model is built with a `RandomForestClassifier`, while customer segmentation is performed using `KMeans` clustering.

## Features

- Interactive Streamlit dashboard
- Churn probability prediction
- Risk labels for low, medium, and high churn risk
- Customer segmentation using clustering
- KPI summary for business analysis
- Data visualization with Matplotlib and Seaborn
- Model persistence with Joblib

## Project Structure

```text
Customer Segmentation Project/
|-- app.py
|-- train.py
|-- WA_Fn-UseC_-Telco-Customer-Churn.csv
|-- models/
|   |-- churn_model.joblib
|   |-- kmeans.joblib
|   `-- preprocessor.joblib
`-- README.md
```

## Dataset

The project uses the Telco Customer Churn dataset:

```text
WA_Fn-UseC_-Telco-Customer-Churn.csv
```

The dataset contains customer account information, service subscriptions, billing details, tenure, and churn status.

## Model Training

The `train.py` script performs these steps:

1. Loads the customer churn dataset.
2. Converts `TotalCharges` into numeric values.
3. Converts the `Churn` column into binary labels.
4. Creates a `service_count` feature from selected service columns.
5. Builds preprocessing pipelines for numeric and categorical features.
6. Trains a Random Forest churn prediction model.
7. Trains a K-Means model for customer segmentation.
8. Saves trained models into the `models/` directory.

To train or retrain the models, run:

```bash
python train.py
```

## Installation

Create and activate a virtual environment:

```bash
python -m venv .venv
.venv\Scripts\activate
```

Install the required packages:

```bash
pip install streamlit pandas numpy scikit-learn joblib matplotlib seaborn
```

## Running the App

From the project directory, run:

```bash
streamlit run app.py
```

The app will open in your browser with the customer churn dashboard.

## Customer Segments

The segmentation page maps model clusters to these business-friendly labels:

- New Customers
- Loyal Customers
- High Value Customers
- At Risk Customers

## Technologies Used

- Python
- Streamlit
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Joblib

## Notes

- Run `train.py` before launching the app if the model files are missing.
- Keep the CSV dataset in the project root because both `train.py` and `app.py` load it from there.
- The trained model files are expected inside the `models/` folder.
