# Workplace Absenteeism Analysis - STT 490

## Project Overview
This project was conducted for **STT 490 (Modern Regression Methods)** (April 2022) to analyze the factors contributing to absenteeism at work. Using a dataset comprised of employee records, the analysis aims to identify the most significant predictors of the number of hours an employee is absent, ranging from medical reasons to disciplinary failures.

The study employs **Generalized Linear Models (GLM)** to explore relationships between absenteeism and various categories of predictors, including demographics, lifestyle choices, and work environment.

## Dataset
The dataset (`Absenteeism_at_work.xls`) includes data on employee absenteeism with the following key features:
* **Response Variable:** `Absenteeism time in hours` (Number of hours absent).
* **Categorical Predictors:** `Reason for absence` (ICD codes/categories), `Social drinker`, `Social smoker`, `Education`, `Disciplinary failure`.
* **Quantitative Predictors:** `Age`, `Body mass index` (BMI), `Distance from Residence to Work`, `Work load Average/day`, `Transportation expense`.

## Methodology

### 1. Exploratory Data Analysis (EDA) & Preprocessing
* **Data Cleaning:** Converted categorical codes (e.g., Seasons, Education, Reason for absence) into factor variables for correct statistical interpretation.
* **Distribution Analysis:** Utilized Histograms and Q-Q plots to assess the normality of the response variable.
* **Transformation:** Identified right-skewness in `Absenteeism time in hours` and applied a **Square Root Transformation** ($\sqrt{y}$) to stabilize variance and improve model fit for the Gaussian GLM.

### 2. Segmented Modeling Approach
To isolate the impact of different variable types, I constructed distinct models for specific factor groups before combining them:
* **Demographic Model:** (`Age`, `BMI`, `Education`)
* **Lifestyle Model:** (`Son`, `Social smoker`, `Social drinker`, `Pet`)
* **Work Environment Model:** (`Distance from Residence`, `Transportation expense`, `Disciplinary failure`, `Work load`)
* **Temporal Model:** (`Month`, `Day of the week`, `Seasons`)

### 3. Advanced Modeling (GLM & Interactions)
* **Full Interaction Model:** A comprehensive model was built to test interaction effects, specifically exploring how the `Reason for absence` interacts with biometrics like `Age` and `BMI`, as well as lifestyle habits (`Social drinker/smoker`).
    * *Example Interaction:* `Reason for absence` $\times$ `Age`
* **Technique:** Used `glm` with `family = "gaussian"` to perform regression analysis on the transformed data.

## Technologies
* **Language:** R
* **Libraries:** `readxl`, `dplyr` (implied for data manipulation), `gam` (for Generalized Additive Models).

## Author
**Nikhil Bhandarkar**
*STT 490 Project*
*Date: April 2022*
