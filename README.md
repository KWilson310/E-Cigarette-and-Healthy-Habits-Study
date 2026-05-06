# E-Cigarette and Healthy Habits Study
Team Members: Elizabeth Greenan, Nicholas Perry, & Kevin Wilson

## Project Details

### Background
This project uses data from the 2024 BRFSS Survey conducted by the CDC to evaluate whether an individual is more likely to use an e-cigarette based on their lifestyle choices.

### Question
Are those with healthier lifestyles less likely to use e-cigarettes than those who may have less healthy lifestyles?

### Hypothesis
We hypothesize a predictive model for e-cigarette usage can be built using health and lifestyle data because unhealthy habits frequently co-occur.

### Prediction
We predict that those with healthier living habits may be less likely to use e-cigarettes due to their desire to live the healthiest lifestyle.

## Dataset Details

### Data and Download
Due to the size of the file, the original dataset is not located in the repository, but the source data used can be downloaded here: https://www.cdc.gov/brfss/annual_data/annual_2024.html

The codebook from the CDC is located in the Documentation folder of the repository.

The data was downloaded as a XPT (SAS Transport) file and imported into R using the haven package. Then, it was written as a .csv file.

At the end of the 3_Data_Cleaning.ipynb script, a cleaned_data.csv will be created. This file is too big to push to GitHub, so users will need to save it locally in order to run scripts 4-7.

At the end of the 5_Pre-Processing.ipynb script, the following csv files will be created: x_train.csv, x_test.csv, y_train.csv, and y_test.csv. Similarly, these files are too big to push to GitHub, so users will need to save these locally. These files will be used to run scripts 8-10.

### Response Variable
The response variable in this dataset is E_Cig_User (renamed from _CURECI3 in the BRFSS dataset). This is a binary response variable, where 0 represents a non e-cigarette user and 1 represents a current e-cigarette user. All missing data was removed from this variable.

### Predictor Variables
There are several predictor variables used for this analysis. They are categorized as demographic, mental health, physical health, lifestyle, and social determinant variables. A complete list can be found in the Data Dictionary, located in the Reports folder of the repository. Note that several of the predictor variables have been renamed for improved readability.


## Analysis Plan

### Imputation
Multivariate Imputation by Chained Equations (MICE) was the imputation method used.

### Pre-Processing & Feature Engineering
Data was split into training and test sets and the ideal ratio was found and implemented. Additionally, one-hot encoding was used to transform all categorical variables to numeric, and scaling was performed.

### Models
Elastic Net Logistic Regression with Lasso (unsupervised for dimension reduction, also used as sueprvised), Elastic Net Logistic Regression with Ridge (supervised), and Random Forest are the models used for this analysis. They were trained on the cleaned, imputed, one-hot encoded, and scaled training dataset.

### Model Performance
When testing model performance, the imputed test set was be used. Metrics such as precision, recall, F1-score, and PR-AUC curves will be used to analyze results and model performance.

## Coding Languages and Required Packages
Due to a SAS import limitation in Python, R was used to write the original dataset to a CSV file. The remaining cleaning, exploratory data analysis, pre-processing, and modeling was conducted in Python.

Required R Packages include:
* haven
  
Required Python Packages include:
* pandas
* numpy
* seaborn
* scipy
* matplotlib
* openpyxl
* tableone
* tabulate
* scikit-learn

## Custom Functions
No custom functions have been created at this time.

## Steps to Run the Project
* Files in the Scripts folder are numbered, representing the order in which they should be run.
* Download the 2024 BRFSS dataset and run the 1_e_cigarette_data.Rmd script to create a CSV file.
* Run the 2_Initial_Variable_Creation.ipynb script.
* Run the 3_Data_Cleaning.ipynb script to clean data. Updated field names can be found in this script.
* Run the 4_Tables_and_Graphs_EDA.ipynb script to perform EDA and create statistical tables for categorical and continuous variables.
* Run the 5_Pre-Processing.ipynb script to perform pre-processing steps such as training and test set split, MICE imputation, one-hot encoding, and scaling.
* Run the 6_Elastic_Net_Logistic_Regression_Lasso_Dimension_Reduction.ipynb script to perform the dimension reduction steps.
* Run the 7_Elastic_Net_Logistic_Regression_Baseline_Lasso_Ridge.ipynb script to perform the baseline Elastic Net model.
* Run the 8_Random_Forest_Model.ipynb script to perform the baseline Random Forest model.
* Run the 9_Elastic_Net_Logistic_Regression_Baseline_Lasso_Ridge_SMOTE.ipynb to perform the baseline Elastic Net model with SMOTE applied.
* Run the 10_Random_Forest_Model_SMOTE.ipynb to perform the Random Forest model with SMOTE and hyperparameter tuning applied.

## Team Member Contributions
Each author contributed equally to the design, coding & development, analysis, and writing of this project. The contribution breakdown can be found below. Additionally, author names are included in each of the scripts, with some having multiple authors.
* Elizabeth Greenan: CSV creation, EDA, Pre-Processing, Random Forest models
* Nicholas Perry: Data Cleaning, EDA, Elastic Net Logistic Regression (Lasso and Ridge)
* Kevin Wilson: EDA, Pre-Processing, feature selection analysis, correlation analysis, Cramer's V analysis
