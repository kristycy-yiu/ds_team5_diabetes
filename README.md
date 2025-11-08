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
Objective: To examine the Early Stage Diabetes Risk Prediction dataset to understand the data and uncover gender related patterns between symptoms and early-stage diabetes.
Method: The data was assessed to identify differences in demographic (i.e. age and gender) and grouped by gender and age using visualizations to highlight key relationships and find differences in each group.  
Findings:
An evaluation of the response variable revealed a moderate class imbalance. Of the 520 patients in the dataset, 320 (~62%) were classified as Positive for diabetes, while 200 (~38%) were classified as Negative. Although not severely imbalanced, this distribution suggests the need for careful model evaluation. Metrics such as precision and recall may provide a more accurate assessment of model performance than accuracy alone. Additionally, care should be taken when interpreting model accuracy and sensitivity, particularly for underrepresented groups./
The dataset consists of 192 Female and 328 Male participants, revealing a clear gender imbalance that could influence model predictions and limit generalizability. This imbalance has direct implications for our business problem since we’re comparing symptom-based predictors across gender. Therefore, models trained on the full dataset may be more heavily influenced by the male symptom observations due to their greater representation. Subsequent analyses may require gender-specific evaluations or consideration of stratification or bootstrapping techniques.

![Correlation Matrix](images/correlation_matrix_heatmap.PNG)

The binary variables were numerically encoded to examine their interrelationships through a correlational matrix. The analysis suggested notable positive associations (such as Polyuria, Polydipsia, and sudden weight loss) between several symptoms and the diabetes outcome variable. While correlation does not imply causation, these relationships support the hypothesis that symptom presentation is a meaningful basis for prediction.

![Age Distribution](images/fig1_age_distribution.PNG)

Figure 1: Age Distribution
The age distribution in the dataset spans from 16 to 90 years. However, most participants fall between 35 and 60 years old, with fewer cases below 30 and above 70. The mean age is approximately 48 years with a median of 47.5 suggesting a fairly symmetric distribution centered around middle adulthood. The standard deviation of 12.15 years suggests moderate variability in age, with no indication of extreme outliers. This broad and balanced age spread is advantageous for our analysis as diabetes risk is known to increase with age and the inclusion of a wide age range improves the generalizability of our findings. In addition, this distribution aligns with the clinical understanding that early-stage diabetes is more prevalent among middle-aged adults, reinforcing the suitability of this dataset for studying early detection risk factors.

![Age and Diabetes Classification by Gender](images/fig2_age_diabetes_scatter.PNG)

Figure 2: Age and Diabetes Classification by Gender
The scatterplot of Age and Diabetes Classification by Gender illustrates how both males and females are affected across similar age ranges, although there are more male participants overall. Preliminary patterns suggest that age may interact differently with gender in predicting diabetes onset. For instance, females show a slightly higher concentration of positive diagnoses at younger ages compared to males, which could warrant further investigation into gender-specific risk factors and symptom presentation. Moreover, positive diagnoses appear more concentrated in individuals between 40 and 55 years old, which may point to midlife as a key period for the onset of diabetes symptoms in both genders.

![Overall Symptom Prevalence Among All Participants](images/fig3_symptom_prevalance.PNG)

Figure 3: Overall Symptom Prevalence Among All Participants 
This bar chart shows the percentage of individuals reporting each symptom across the full dataset. Weakness, polyuria, and itching were the most commonly reported symptoms, whereas irritability, genital thrush, and obesity were least prevalent. These findings suggest that general fatigue and urinary changes are widespread in the population and may warrant closer investigation in diabetes risk screening.


![Symptom Prevalence between Diabetic and Non-Diabetic Participants](images/fig4_symptom_prevelance_heatmap.PNG)

Figure 4: Symptom Prevalence between Diabetic and Non-Diabetic Participants
This heatmap shows the prevalence of common diabetes-related symptoms among diabetic and non-diabetic participants. The most distinct differences are observed for polyuria and polydipsia, with diabetics exhibiting these symptoms over ten times more frequently than non-diabetics, suggesting potential predictive strength. Other symptoms such as sudden weight loss, weakness, and partial paresis are also notably elevated in diabetic individuals. The remaining variables show more even distributions or low variance, which may limit their predictive relevance. These initial observations provide an early indication of which symptoms may emerge as statistically significant predictors during modeling. From the perspective of the business case, these results reinforce the importance of early recognition of metabolic and neurological symptoms in diabetes screening.

![Symptom Prevalence among Diabetic Participants by Gender](images/fig5_symptom_prevalance.PNG)

Figure 5: Symptom Prevalence among Diabetic Participants by Gender
This heatmap compares symptom frequencies between male and female participants with diabetes. While both genders show high rates of polyuria, polydipsia, and weakness, females report higher frequencies of sudden weight loss and partial paresis, whereas males more often report genital thrush, alopecia, and irritability. These differences suggest gender-specific patterns in the presentation of early-stage diabetes symptoms.

![Top Gender-Based Differences among Diabetic Participants](images/fig6_gender_based_barchart.PNG)

Figure 6: Top Gender-Based Differences among Diabetic Participants
The chart displays the absolute percentage difference in symptom prevalence between male and female individuals with diabetes. The largest disparities occur in alopecia, genital thrush, and partial paresis, indicating that dermatological and neuromuscular symptoms exhibit notable gender-specific patterns. Core metabolic symptoms such as polyuria, polydipsia, and weakness show minimal gender variation.

![Symptom Prevalence by Diabetes Status](images/fig7_symptom_prevalance_barchart.PNG)

Figure 7: Symptom Prevalence by Diabetes Status
The bar chart displays the proportion of patients reporting each symptom, grouped by diabetes classification. Polyuria, Polydipsia, and Sudden Weight Loss show the strongest associations with diabetes-positive cases, with over 60% of diabetic patients experiencing these symptoms. In contrast, symptoms like Alopecia and Obesity are more evenly distributed or more prevalent among non-diabetic individuals. These findings suggest that a subset of symptoms may have higher predictive power for diabetes diagnosis. 


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
