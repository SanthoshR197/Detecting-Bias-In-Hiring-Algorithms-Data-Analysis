# Detecting Bias in Hiring Algorithms: A Comprehensive Data Analysis Report

## 📋 Table of Contents
1. [Overview](#-overview)
2. [Problem Statement](#-problem-statement)
3. [Dataset Description](#-dataset-description)
4. [Methodology](#-methodology)
    - [Data Preprocessing](#data-preprocessing)
    - [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
    - [Bias Detection & Statistical Analysis](#bias-detection--statistical-analysis)
    - [Predictive Modeling](#predictive-modeling)
5. [Key Insights & Results](#-key-insights--results)
6. [Fairness Metrics](#-fairness-metrics)
7. [Conclusion & Recommendations](#-conclusion--recommendations)
8. [Technologies Used](#-technologies-used)

---

## 🌟 Overview
In the modern corporate world, automated hiring algorithms are increasingly used to filter candidates. However, if these algorithms are trained on biased historical data, they can perpetuate systemic inequalities. This project performs an end-to-end data analysis on recruitment data to identify patterns, trends, and potential biases (gender, age, education) in the shortlisting process.

## 🎯 Problem Statement
The primary objective is to evaluate whether a recruitment process is fair and unbiased. By analyzing candidate attributes such as gender, age, experience, and screening scores against their shortlisting outcomes, we aim to uncover hidden biases and ensure that the selection process is based solely on merit.

## 📊 Dataset Description
The analysis utilizes the **"Recruitment Bias and Fairness AI Dataset"** sourced from Kaggle.
- **Total Records:** 2,000 candidates
- **Features:**
  - `gender`: Male / Female
  - `age`: Candidate's age (21 - 49)
  - `education_level`: High School, Bachelors, Masters, PhD
  - `experience_years`: Years of relevant professional experience
  - `screening_score`: Numerical score from initial technical/HR screening
- **Target Variable:**
  - `shortlisted`: Binary (1 = Yes, 0 = No)

---

## 🛠 Methodology

### Data Preprocessing
- **Cleaning:** Standardized string values (case correction) and verified zero null/duplicate entries.
- **Encoding:** Applied Label Encoding for binary features (`gender`) and One-Hot Encoding for multi-categorical features (`education_level`).
- **Scaling:** Used `StandardScaler` to normalize numerical features (`age`, `experience_years`, `screening_score`) for model stability.
- **Categorization:** Grouped age into '20s', '30s', and '40s' for granular demographic analysis.

### Exploratory Data Analysis (EDA)
- **Visualizations:** Generated heatmaps for missing values and correlations, count plots for demographic distributions, and box plots for outlier detection.
- **Correlation Analysis:** Identified that `screening_score` has the strongest positive correlation with being `shortlisted`.

### Bias Detection & Statistical Analysis
- **Gender Bias:** Compared shortlisting rates and mean screening scores between Male and Female candidates.
- **Statistical Testing:** Conducted **T-Tests** for numerical differences and **Chi-Square Tests** for categorical dependencies to determine if observed differences are statistically significant.

### Predictive Modeling
- **Algorithm:** Trained a **Random Forest Classifier** to predict shortlisting outcomes.
- **Evaluation:** Assessed performance using Precision, Recall, F1-Score, and AUC-ROC curves.
- **Feature Importance:** Analyzed which factors (e.g., technical score vs. gender) the model relies on most for its predictions.

---

## 📈 Key Insights & Results
- **Education Impact:** Candidates with **PhD** degrees show a significantly higher shortlisting rate compared to other groups.
- **Primary Driver:** The `screening_score` is the most significant predictor of success, suggesting a merit-heavy process at first glance.
- **Gender Trends:** Analysis shows the distribution of scores between genders; statistical tests were used to verify if any slight variance in shortlisting rate constitutes systemic bias.

## ⚖ Fairness Metrics
To quantify bias, the following metrics were calculated:
1. **Disparate Impact Ratio:** The ratio of the selection rate of the "unprivileged" group to the "privileged" group (target > 0.8).
2. **Demographic Parity Difference:** The difference in shortlisting probability between different demographic groups.

## 🏁 Conclusion & Recommendations
The study concludes that while technical merit (screening score) is a high priority, there are subtle variances across demographic groups that warrant attention. 
**Recommendations:**
- **Blind Screening:** Remove gender and age indicators from the data before feeding it into the automated model.
- **Score Auditing:** Periodically audit technical tests to ensure questions don't inadvertently favor specific educational backgrounds or age groups.
- **Diverse Training Data:** Supplement training sets with balanced samples to prevent the "feedback loop" of historical bias.

## 💻 Technologies Used
- **Languages:** Python
- **Libraries:** 
  - `Pandas`, `NumPy` (Data Manipulation)
  - `Matplotlib`, `Seaborn` (Data Visualization)
  - `Scikit-learn` (Machine Learning & Preprocessing)
  - `SciPy` (Statistical Testing)

---
*Created as part of a Data Analysis project on Algorithmic Fairness.*
