# 🚗 Car Price Prediction Project
This repository contains the R code for a comprehensive data analysis and modeling project focused on predicting car prices (`Price`) using a dataset of vehicle features. The workflow includes meticulous data cleaning, feature engineering, exploratory analysis, and the development of robust Generalized Linear Models (GLMs).

### 🗄️ Project Files

* `Project_car.qmd`: The main analysis file containing all R code for data cleaning, EDA, model building, and diagnostics.
* `Ololade_Akinsanola_Project.pdf`: The final academic report detailing the methodology, results, model critiques, and future work.
* `Data/CarPrice.csv`: The raw dataset used for the analysis.

### 🛠️ Setup and Prerequisites

To replicate this analysis, you must have the R programming language installed. The following R packages are required:


# Required R Libraries
install.packages(c("tidyverse", "broom", "car", "lmtest", "zoo"))

# 📈 Methodology and Key Steps

The analysis, documented in Project_car.qmd, follows a structured data science pipeline:

1 Data Preparation and Feature Engineering

Cleaning: Numeric features like Mileage, Levy, and Engine.volume were cleaned by removing non-numeric characters and standardizing formats.

Imputation: Missing values were handled by imputing the median for numeric variables (Price, Levy) and the mode for categorical variables (Manufacturer, Model).

Outlier Handling: Outliers were capped using the Interquartile Range (IQR) method) to ensure model robustness.

Feature Creation: A key feature, Age (calculated as 2024 - Prod. year), was introduced to capture depreciation effects.

Grouping: Categorical variables (e.g., Color, Fuel.type) were grouped into fewer, more meaningful categories to improve model interpretability.

2. Exploratory Data Analysis (EDA)

A representative subset (cars_red) was created using stratified sampling based on Fuel.type to maintain the original distribution.

Descriptive statistics and visualizations (histograms, boxplots, scatter plots) were used to analyze variable distributions and their relationships with the target variable, Price.

3. Model Building and Selection

The project explored several models, ultimately settling on a Generalized Linear Model (GLM) to account for the non-linear relationship between predictors and price.

Target Variable Transformation: The target variable, Price, was log-transformed (log(Price)) to stabilize variance and improve linearity.

Final Model: The chosen GLM incorporates main effects, polynomial terms (I(Engine.volume^2)), and interaction terms (Fuel.type:Engine.volume, Age:Mileage) to capture complex, non-linear patterns influencing the price.

Selection Criteria: Models were evaluated and selected using AIC (Akaike Information Criterion) and BIC (Bayesian Information Criterion).

# 4. Model Diagnostics

Rigorous diagnostic checks were performed to evaluate the final model's adherence to classical assumptions for Generalized Linear Models (GLMs).

Multicollinearity Assessment

Test: The Variance Inflation Factor (VIF) was used.

** Result: The VIF analysis indicated the presence of some degree of multicollinearity among the predictors. This suggests that while the model is predictive, the individual coefficient interpretations should be made cautiously, as their values may be unstable.

# Homoscedasticity Assessment

Test: The Breusch-Pagan Test (bptest) was conducted on the residuals.

Result: The test was statistically significant (p≤0.05), indicating that the assumption of homoscedasticity was violated. The model exhibits heteroscedasticity , meaning the spread of the errors is not uniform.

## Normality of Residuals Assessment

Test: The Kolmogorov-Smirnov Test (ks.test) was applied to the residuals.

Result: The test returned a statistically significant result (p≤0.05), leading to the rejection of the null hypothesis that the residuals are normally distributed. This indicates that the normality assumption was violated.

## Summary of Diagnostic Findings

Multicollinearity: Some Present (VIF). Implication: Coefficient estimates may be unstable.

Homoscedasticity: Violated (Breusch-Pagan Test). Implication: Standard errors and p-values may be unreliable.

Normality of Residuals: Violated (Kolmogorov-Smirnov Test). Implication: Inference (confidence intervals) may be inaccurate.

# 💡 Key Findings

The model achieved a Pseudo-R-squared of approximately 44.8% on the log-transformed price.

Age and Mileage are consistently strong predictors, showing the expected negative association with car price (i.e., older cars with more mileage are cheaper).

The use of polynomial and interaction terms significantly improved model fit over a simple linear model.

# 🚀 Future Work

Despite the violations of classical assumptions, the model captures a substantial portion of the variance. These diagnostic results strongly reinforce the recommendation for future work to incorporate more robust modeling techniques:

Applying advanced Regularization techniques (LASSO/Ridge) to manage multicollinearity.

Exploring non-linear machine learning algorithms such as Random Forest or Support Vector Machines (SVM) for improved predictive accuracy.

Collecting additional features (e.g., car market popularity, regional sales data) to enhance model explanatory power.
