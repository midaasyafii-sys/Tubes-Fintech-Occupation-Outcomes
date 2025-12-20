# Tubes-Fintech-Occupation-Outcomes
Tugas Besar Mata Kuliah Analisa Keputusan untuk Teknologi Finansial 
# Financial Capability Prediction : Occupation & Outcome Analysis

## Project Overview
This project focuses on **Financial Decision Analysis** within the Fintech sector. Specifically, it aims to predict an individual's financial capability (Capacity to Repay) based on their socio-economic profile, with a strong emphasis on **Occupation**.

Using the **Adult Census Income Dataset**, this project addresses the strategic trade-off in credit scoring between **Model Accuracy** and **Decision Interpretability**. We perform a comparative analysis between **Decision Tree** (White-box model) and **Random Forest** (Ensemble model) to determine the best approach for mitigating credit risk.

## Dataset
The project utilizes the **Occupation & Outcomes** from kaggle, which serves as a proxy for creditworthiness data.
* **Source :** Census Bureau data.
* **Features :** Socio-demographic attributes including `Occupation`, `Workclass`, `Education`, `Age`, and `Hours-Per-Week`.
* **Target :** `Income` level (`>50K` vs `<=50K`). In this financial context, `>50K` represents high repayment capacity (Low Risk), while `<=50K` represents lower capacity (High Risk).
* **Challenges :** The raw data contains significant missing values and class imbalance, simulating real-world financial data issues.

## Methods Used
This project follows a rigorous Data Science lifecycle:

* **Data Preprocessing :**
    * Handling missing values (Imputation using Median/Mode).
    * Cleaning data inconsistencies.
* **Exploratory Data Analysis (EDA) :**
    * Visualizing the distribution of Income across different Occupations.
    * Analyzing statistical summaries to understand risk factors.
* **Data Preparation :**
  * Label Encoding for categorical variables.
  * **SMOTE (Synthetic Minority Over-sampling Technique)** to address class imbalance and prevent model bias.
* **Modeling Strategy :**
    * **Decision Tree :** To extract explicit decision rules (Explainability).
    * **Random Forest :** To maximize prediction accuracy and stability.
* **Optimization Plan :** Hyperparameter tuning with multiple scenarios to find optimal model configuration.

---
*Note: This repository is currently under active development. Results and deployment instructions will be updated soon.*
