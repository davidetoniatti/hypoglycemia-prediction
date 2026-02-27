# Predicting Hypoglycemic Events in Diabetic Patients

This is a basic machine learning project focused on predicting hypoglycemic events using sparse blood glucose measurements and clinical records from diabetic patients.

## Project Overview
This project implements a binary classification pipeline to identify potential hypoglycemic events (defined as blood glucose < 70 mg/dL). It is a simple and basic exploration of how historical patient data can be used to predict short-term clinical risks.

## Dataset
The analysis is based on the [UCI Machine Learning Repository Diabetes Dataset](archive.ics.uci.edu/dataset/34/diabetes), which contains records from 70 diabetic patients. The data is characterized by sporadic measurements taken a few times per day, with an average gap of approximately 7 hours between readings.

## Methodology: Sliding Window Approach
Due to the irregular sampling of the data, the project does not use fixed-time intervals. Instead, it utilizes a sliding window approach based on the sequence of observations:

- Lookback ($N$). The model looks at the **last $N$ glucose measurements** along with associated insulin and behavioral data.
- Prediction ($M$). The model predicts the likelihood of a hypoglycemic event occurring within the **next $M$ measurements**.

This $N$-to-$M$ mapping allows the model to capture glycemic dynamics despite the high sparsity of the dataset.

## Features
The model utilizes 12 features extracted from the lookback window, including:
- **Glucose Dynamics.** Last value, mean, minimum, standard deviation, and trend.
- **Insulin.** Total dosage administered within the window.
- **Behavioral Context.** Presence of meals (normal or small) and intense physical activity.
- **Temporal Context.** Time of day categorized into four slots.

## Models and Performance
The project compares two standard algorithms:
- **Logistic Regression** (baseline).
- **Random Forest.** Captures non-linear relationships.

The models were evaluated using patient-level cross-validation.

## Requirements

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

