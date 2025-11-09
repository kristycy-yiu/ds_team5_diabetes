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

### Literature Search
A literature search will be conducted to provide theoretical grounding for the variables, identify any known confounders, and support interpretation for statistical results. The information on confounders will be used to inform adjustment variables in our regression model.

Search #1
Database: PubMed
Search terms: 
("type 2 diabetes mellitus"[MeSH Terms] OR "type 2 diabetes" OR "diabetes mellitus, type 2")
AND ("sex differences" OR "gender differences" OR "male female comparison")
AND ("risk factors" OR predictors OR "clinical features" OR symptoms OR determinants)
AND (humans[MeSH Terms])
AND (English[lang])
Publication date: within last 5 years 
Language: English
Number of search results: 283

Search #2
Database: Google Scholar
Search terms: 
("type 2 diabetes mellitus"[MeSH Terms] OR "type 2 diabetes" OR "diabetes mellitus, type 2")
AND ("sex differences" OR "gender differences" OR "male female comparison")
AND ("risk factors" OR predictors OR "clinical features" OR symptoms OR determinants)
AND (humans[MeSH Terms])
AND (English[lang])
Publication date: since 2021
Language: English
Number of search results: 15 

Searches #1 and 2 did not yield sufficient relevant results so the search strategy (search terms) was revised for Search #3.

Search #3
Database: PubMed
Search terms: 
("Diabetes Mellitus, Type 2"[Mesh]) 
AND ("early-onset"[Title/Abstract] OR "premature"[Title/Abstract] OR "middle-aged"[Mesh] OR "adult"[Mesh]) 
AND ("Risk Factors"[Mesh] OR predictor*[Title/Abstract] OR "clinical features"[Title/Abstract] OR determinants[Title/Abstract] OR "associated factors"[Title/Abstract]) 
AND (Age[Mesh] OR "Sex Characteristics"[Mesh] OR "Obesity"[Mesh] OR "Body Mass Index"[Mesh] OR polyuria[Title/Abstract] OR polydipsia[Title/Abstract] OR "sudden weight loss"[Title/Abstract] OR weakness[Title/Abstract] OR polyphagia[Title/Abstract])
AND ("cohort study"[Publication Type] OR "case-control study"[Publication Type] OR "observational study"[Publication Type])
Publication date: within last 5 years
Language: English
Number of search results: 65

Search #3 also did not yield sufficient relevant results so Search #4 will be developed and presented in the final submission. 

### Descriptive and Exploratory Data Analysis
Exploratory data analysis will be conducted to understand the demographic and clinical characteristics of the population.
- Descriptive statistics: Summarize key variables (e.g., mean age, gender distribution, and prevalence of each symptom).
- Cross-tabulations: Compare symptom frequencies between diabetic and non-diabetic individuals, as well as across genders.
- Visualization: Use bar plots, scatterplots, and heatmaps to identify potential patterns or correlations between features and diabetes status.
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
A preliminary analysis of the dataset was conducted to evaluate its structure, suitability for analysis, and potential considerations relevant to our overarching goal: to explore and identify significant demographic variables and clinical predictors of early-onset diabetes by gender to support targeted prevention and early intervention strategies.

The dataset consists of 520 observations and 17 variables, including one outcome variable and a combination of demographic and symptom-based predictors. The response variable: class, indicates the presence or absence of early-stage diabetes classified as Positive or Negative. Predictor variables include demographic factors (Age and Gender) and 14 binary symptom indicators (e.g. Polyuria, Polydipsia, sudden weight loss, visual blurring, etc.).

All symptom-related variables and the outcome variable are recorded as binary categorical values (Yes/No), while Age is a numeric variable. A thorough review of the dataset using standard data integrity practices indicated that there were no missing values. All variables contained complete data for all 520 observations. The dataset is clean and does not require imputation or substantial preprocessing aside from applying standard data encoding methods to categorical variables within the dataset (e.g. transforming Yes/No to 1 and 0).

---

## Exploratory Data Analysis
**Objective:** To examine the Early Stage Diabetes Risk Prediction dataset to understand the data and uncover gender related patterns between symptoms and early-stage diabetes.

**Method:** The data was assessed to identify and summarize key differences in demographic (i.e. age and gender) and grouped by gender and age using visualizations to highlight key relationships and find differences in each group.  

**Findings:**



![Overall Symptom Prevalence](images/overall_symptom_prevelance.png)
**Figure 6: Overall Symptom Prevalence Among All Participants**
  This bar chart shows the percentage of individuals reporting each symptom across the full dataset. Weakness, polyuria, and itching were the most commonly reported symptoms, whereas irritability, genital thrush, and obesity were least prevalent. These findings suggest that general fatigue and urinary changes are widespread in the population and may warrant closer investigation in diabetes risk screening.


![Symptom Prevalence between Diabetic and Non-Diabetic Participants](images/symptom_prevalence_among_diabetic_by_gender.png)
**Figure 7: Symptom Prevalence between Diabetic and Non-Diabetic Participants**
  This heatmap shows the prevalence of common diabetes-related symptoms among diabetic and non-diabetic participants. The most distinct differences are observed for polyuria and polydipsia, with diabetics exhibiting these symptoms over ten times more frequently than non-diabetics, suggesting potential predictive strength. Other symptoms such as sudden weight loss, weakness, and partial paresis are also notably elevated in diabetic individuals. The remaining variables show more even distributions or low variance, which may limit their predictive relevance. These initial observations provide an early indication of which symptoms may emerge as statistically significant predictors during modeling. From the perspective of the business case, these results reinforce the importance of early recognition of metabolic and neurological symptoms in diabetes screening.


![Symptom Prevalence among Diabetic Participants by Gender](images/symptom_prevalence_diabetic_non_diabetic_participants.png)
**Figure 8: Symptom Prevalence among Diabetic Participants by Gender**
  This heatmap compares symptom frequencies between male and female participants with diabetes. While both genders show high rates of polyuria, polydipsia, and weakness, females report higher frequencies of sudden weight loss and partial paresis, whereas males more often report genital thrush, alopecia, and irritability. These differences suggest gender-specific patterns in the presentation of early-stage diabetes symptoms.


![Symptom Prevalence among Diabetic Participants by Gender](images/top_gender_differences_among_diabetic.png)
**Figure 9: Top Gender-Based Differences among Diabetic Participants**
  The chart displays the absolute percentage difference in symptom prevalence between male and female individuals with diabetes. The largest disparities occur in alopecia, genital thrush, and partial paresis, indicating that dermatological and neuromuscular symptoms exhibit notable gender-specific patterns. Core metabolic symptoms such as polyuria, polydipsia, and weakness show minimal gender variation.


![Symptom Prevalence by Diabetes Status](images/sym_prev_status.png)
**Figure 10: Symptom Prevalence by Diabetes Status**
  The bar chart displays the proportion of patients reporting each symptom, grouped by diabetes classification. Polyuria, Polydipsia, and Sudden Weight Loss show the strongest associations with diabetes-positive cases, with over 60% of diabetic patients experiencing these symptoms. In contrast, symptoms like Alopecia and Obesity are more evenly distributed or more prevalent among non-diabetic individuals. These findings suggest that a subset of symptoms may have higher predictive power for diabetes diagnosis. 

---

## Risks, Limitations, & Unknowns

### Risks
Gender imbalance: With a higher number of male cases, the gender imbalance may lead to biased model predictions, risking reduced accuracy for female patients and difficulty in detecting subtle differences between genders. We will mitigate this risk using bootstrapping to oversample the underrepresented female cases to create a more balanced training set.

Confounders: If confounders (e.g., BMI) are not accounted for, the model could be biased and lead to incorrect conclusions about gender differences. To mitigate this risk, we will analyze the subgroups of confounders separately.

### Limitations
Data generalizability: The data may not be generalizable to the Canadian population as it is based on data collected in Sylhet, Bangladesh.

Unclear definitions of clinical features: Clinical features including “sudden weight loss”, “weakness”, “partial paresis”, “irritability”, “delayed hearing”, “visual blurring”, and “itching” are not clearly defined in the dataset. Thresholds for these variables or standardized measurement scales are not provided, which limits our ability to determine their severity or to ensure consistent assessment across patients. This may limit our ability to provide appropriate recommendations regarding these factors. 

### Unknowns
Other possible predictors of diabetes: Literature has shown that race/ethnicity, acculturation, tobacco smoking, education level, and marital status are also predictive of early onset diabetes. Without information on these variables in our dataset, it is unknown whether the clinical features that we’ve identified are the most significant predictors or if there are more prominent predictors that we have not yet explored.

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
