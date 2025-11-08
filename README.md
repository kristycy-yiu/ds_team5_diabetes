# Early Stage Diabetes Risk Prediction Analysis

## DS Team 5 Members
* Kristy Yiu
* Rebecca Laundos
* Lamoya Waldman
* Samantha Sathaseevan

## Contents

* [Project Overview & Purpose](#project-overview--purpose)
* [Goals & Objectives](#goals--objectives)
* [Methodology](#methodology)
* [Data Preparation](#data-preparation)
* [Exploratory Data Analysis](#exploratory-data-analysis)
* [Risks, Limitations, & Unknowns](#risks-limitations--unknowns)
* [Regression Analysis](#regression-analysis)
* [Conclusions & Discussion](#conclusions--discussion)

---

## Project Overview & Purpose
**Source:** [UCI Machine Learning Repository - Early Stage Diabetes Risk Prediction Data](https://archive.ics.uci.edu/dataset/529/early+stage+diabetes+risk+prediction+dataset)

This project uses the Early Stage Diabetes Risk Prediction dataset to explore and identify whether there is a gender difference between significant predictors for early stage diabetes. The goal of this project is to reduce the long term impact of diabetes on the healthcare system by identifying gender-based differences in symptom presentation to enable primary care physicians to intervene earlier on with appropriate follow-up, triage, and prevention plans, as needed. 

**Business Problem:** 
Diabetes is a rapidly growing public health and economic challenge, driving substantial long-term costs for healthcare systems due to complications, hospitalizations, and chronic disease management. Early detection and intervention are critical to reducing these burdens, yet many cases of early-stage diabetes go undiagnosed until symptoms become severe.

A key obstacle in achieving timely diagnosis is the lack of gender-sensitive risk assessment tools. Current screening models and predictive algorithms often treat male and female patients as a single homogeneous group, overlooking potential differences in how symptoms present and progress across genders. This one-size-fits-all approach may result in delayed identification of at-risk individuals, inefficient resource utilization, and missed opportunities for early preventive care.

This project addresses this gap by using the Early Stage Diabetes Risk Prediction dataset to explore and identify gender-based differences in the predictors of early-stage diabetes. Understanding how symptom patterns vary between men and women can help primary care providers and healthcare organizations:
* Develop more precise screening models that tailor risk prediction to patient demographics.
* Improve triage and follow-up protocols for individuals presenting with early diabetes symptoms.
* Reduce long-term healthcare costs by enabling earlier, gender-informed interventions that prevent complications.
  
By uncovering actionable insights into gender differences in symptom presentation, this analysis supports evidence-based decision-making and strengthens healthcare systems’ ability to deliver proactive, personalized, and cost-effective diabetes management strategies.

---

## Goals & Objectives
The overarching project goal is to explore and identify significant demographic variables and clinical predictors of early-onset diabetes by gender to support targeted prevention and early intervention strategies.

To achieve the project goal, we have created the following objectives:
* Identify theoretically plausible confounders through literature and confirm whether these relationships appear in your dataset through exploratory analysis
* Evaluate demographic variables (age and gender) as predictors of early-onset diabetes using logistic regression to understand the baseline associations
* Evaluate clinical features (polyuria, polydipsia, sudden weakness, etc.) as predictors of early-onset diabetes to see how clinical symptoms relate independently to the condition
* Test for potential confounders and identify the variables which need to be adjusted
* Develop a combined, adjusted model with the most prominent demographic and clinical predictors to evaluate whether gender differences persist after adjustment

The most significant predictors are the ones that remain statistically significant after adjustment.

---

## Methodology
This project applies a data-driven approach to explore gender-based differences in predictors of early-stage diabetes using the Early Stage Diabetes Risk Prediction dataset. The methodology follows a structured analytical pipeline to ensure accuracy, interpretability, and reproducibility of results.

### Data Preparation/Cleaning
Before any analysis, the dataset will be assessed for completeness, consistency, and accuracy.
- Handling missing data: Verify if there are any null or inconsistent entries (e.g., blank cells or typos in “Yes/No” fields) and address them through imputation or removal as appropriate.
- Data type conversion: Convert categorical “Yes/No” responses into binary numerical values (1/0) and encode gender as a binary or categorical variable.
- Normalization and consistency checks: Confirm uniform variable naming, ensure correct value ranges (e.g., realistic age values), and identify potential outliers.
- Reproducibility: All cleaning steps will be implemented programmatically in Python to allow transparent and repeatable preprocessing.

### Descriptive and Exploratory Data Analysis
Exploratory data analysis will be conducted to understand the demographic and clinical characteristics of the population.
- Descriptive statistics: Summarize key variables (e.g., mean age, gender distribution, and prevalence of each symptom).
- Cross-tabulations: Compare symptom frequencies between diabetic and non-diabetic individuals, as well as across genders.
- Visualization: Use bar plots, histograms, and heatmaps to identify potential patterns or correlations between features and diabetes status.
- Preliminary insights: Identify which symptoms appear most common or distinctive between males and females diagnosed with diabetes.

### Regression Analysis and Validation
A statistical modeling approach will be applied to identify significant predictors of early-stage diabetes and assess gender-based differences.
- Logistic Regression (Primary Model)
  - Purpose: To estimate the relationship between predictor variables (age, symptoms) and the likelihood of diabetes (dependent variable: class).
  - Approach:
    - Perform logistic regression on the full dataset to determine overall predictors.
    - Conduct stratified regression analyses for males and females to compare significant predictors across genders.
    - Include interaction terms (e.g., Gender × Symptom) to test whether the relationship between symptoms and diabetes risk differs by gender.
  - Outputs: Odds ratios, confidence intervals, and p-values will be used to interpret the relative importance and significance of each predictor.

- Model Validation
  - Train-test split: The dataset will be split into training (80%) and testing (20%) sets to evaluate model generalizability.
  - Performance metrics: Assess model accuracy, precision, recall, F1-score, and ROC-AUC to ensure robust predictive performance.
  - Multicollinearity checks: Variance Inflation Factor (VIF) will be computed to ensure predictors are not highly correlated.

### Visualization of Findings
Visual analytics will be used to communicate insights clearly and effectively:
- Coefficient plots: Display relative influence of each predictor by gender.
- ROC curves: Compare model performance between male and female subgroups.
- Heatmaps and pair plots: Highlight relationships between symptoms and diabetes status.
- Summary visuals: Develop side-by-side charts to illustrate differences in key predictors across genders.

All visualizations will follow best practices in clarity, labeling, and accessibility to support interpretation by both technical and clinical stakeholders.

### Technical Considerations
Programming Environment
- Language: Python
- Development tools: Visual Studio Code for code execution, documentation and visualization

Libraries and their Purpose:
- NumPy: Efficient numerical operations and array manipulations.
- Pandas: Data loading, cleaning, and structured manipulation using DataFrames.
- Scikit-learn (preprocessing & modeling): Encoding categorical variables, splitting data, building logistic regression models, and evaluating performance metrics.
- Statsmodels: Statistical inference and regression diagnostics (e.g., p-values, odds ratios, and confidence intervals).
- Matplotlib: Creating foundational visualizations for trends, distributions, and comparisons.
- Seaborn: High-level statistical visualization for clear and aesthetically appealing plots (e.g., heatmaps, countplots).

---

## Data Preparation


---

## Exploratory Data Analysis


---

## Risks, Limitations, & Unknowns

### Risks

### Limitations

### Unknowns


---

## Regression Analysis


---

## Conclusions & Discussion


---

## Team Member Video Links

| Name                 | Links |
|----------------------|-------|
| Kristy Yiu           |       |
| Rebecca Laundos      |       |
| Lamoya Waldman       |       |
| Samantha Sathaseevan |       |
