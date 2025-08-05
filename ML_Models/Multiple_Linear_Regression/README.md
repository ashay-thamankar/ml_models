# 📘 Multiple Linear Regression – Detailed Explanation

## 🔍 Overview

**Multiple Linear Regression (MLR)** is an extension of simple linear regression that models the relationship between **one dependent variable** and **two or more independent variables**. It helps in understanding how multiple features jointly influence the outcome.

---

## 📐 Equation

The general equation of Multiple Linear Regression is:

  **y = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ + ε**

Where:

* **y** = Dependent variable (target)
* **x₁, x₂, ..., xₙ** = Independent variables (features)
* **β₀** = Intercept (value of y when all x’s are 0)
* **β₁...βₙ** = Coefficients for each feature
* **ε** = Error term (residual)

---

## ⚙️ How It Works

1. **Objective**: Find the best-fitting hyperplane in n-dimensional space that minimizes the prediction error.

2. **Learning Method**: Uses **Ordinary Least Squares (OLS)** to estimate the coefficients.

   * It minimizes the **sum of squared differences** between actual and predicted values.
   * The optimization problem:
        **minimize Σ(yᵢ - ŷᵢ)²**

3. **Fitting the Model**:

   * Calculates optimal values of **β** that minimize this squared error.
   * Each **β** indicates the effect of a unit change in that variable, keeping others constant.

---

## 🔎 Assumptions of Multiple Linear Regression

1. **Linearity**: Relationship between the dependent variable and predictors is linear.
2. **Independence**: Observations are independent of each other.
3. **Homoscedasticity**: Constant variance of residuals across all levels of the independent variables.
4. **No multicollinearity**: Independent variables should not be highly correlated with each other.
5. **Normality of residuals**: Errors should be normally distributed.

---

## 📊 Evaluation Metrics

| Metric          | Description                                            |
| --------------- | ------------------------------------------------------ |
| **R² Score**    | Proportion of variance in target explained by features |
| **Adjusted R²** | Adjusted for the number of predictors used             |
| **MAE**         | Mean Absolute Error                                    |
| **MSE**         | Mean Squared Error                                     |
| **RMSE**        | Root Mean Squared Error                                |

---

## ✅ Advantages

* Considers **multiple factors** simultaneously.
* Easy to **interpret** and implement.
* Allows understanding of **relative importance** of each variable.
* Works well when assumptions are met.

---

## ⚠️ Limitations

* Assumes **linear** relationships (can underperform in complex real-world data).
* **Multicollinearity** among features can distort results.
* **Outliers** can heavily affect the model.
* Doesn’t capture **non-linear patterns** unless engineered into features.

---

## 🎯 Applications

* Predicting **house prices** based on size, location, number of rooms, etc.
* Estimating **salary** based on experience, education level, location, etc.
* **Marketing ROI analysis** based on ad spend, channel, duration, etc.
* Predicting **medical costs** based on age, BMI, smoking status, etc.
* **Energy consumption** forecasting using temperature, occupancy, and device usage.

---

## 🧠 When to Use Multiple Linear Regression?

Use MLR when:

* You have more than one feature affecting your target variable.
* You want to **quantify the effect** of each feature.
* Relationships are **additive and linear**.

---

## 🛠️ Model Improvement Tips

* **Feature Engineering**: Create interaction terms or polynomial features if relationships aren’t purely linear.
* **Check Multicollinearity**: Use **VIF (Variance Inflation Factor)** to detect it.
* **Standardization**: Scale features if they differ in units to improve interpretability and convergence.
* **Residual Analysis**: Always analyze residual plots to check for assumption violations.

---

# 📘 Multiple Linear Regression – Economic Index Case Study

## 🔍 Problem Statement

The goal of this notebook is to **predict the Economic Index Price** based on two key macroeconomic variables:

* **Interest Rate**
* **Unemployment Rate**
---

## ⚙️ Steps Followed

### 1. **Data Loading & Cleaning**

* Imported required libraries.
* Read the CSV file using pandas.
* Dropped unnecessary columns like `Unnamed: 0`, `year`, and `month`.

### 2. **Exploratory Data Analysis (EDA)**

* Used **pair plots** and **correlation matrices** to understand relationships between variables.
* Found strong:

  * Positive correlation between **interest\_rate** and **index\_price**.
  * Negative correlation between **unemployment\_rate** and **index\_price**.

### 3. **Feature Selection**

* **Independent variables (X):** `interest_rate`, `unemployment_rate`
* **Target variable (y):** `index_price`

### 4. **Train-Test Split**

* Split data into **75% training** and **25% testing** using `train_test_split()`.

### 5. **Data Scaling**

* Applied **StandardScaler** to normalize input features.

### 6. **Model Training**

* Used `LinearRegression()` from `sklearn` to train the model on the scaled training data.

### 7. **Cross-Validation**

* Performed 3-fold **cross-validation** using negative MSE scoring to validate model performance.

### 8. **Model Evaluation**

* Predicted values for test data.
* Calculated performance metrics:

  * **MSE**: 8108.57
  * **MAE**: 73.80
  * **RMSE**: 90.05
  * **R² Score**: 0.7591
  * **Adjusted R²**: 0.5986

### 9. **Residual Analysis**

* Plotted residuals (y\_test - y\_pred) to check assumptions:

  * **Histogram** using `sns.displot()` showed near-normal distribution.
  * **Scatter plot of residuals vs. predictions** indicated no clear patterns.

### 10. **OLS Summary using Statsmodels**

* Built a second model using `statsmodels.api.OLS`.
* Displayed detailed summary table (coefficients, p-values, R², etc.).
* Interpretation:

  * Coefficients were statistically insignificant (high p-values).
  * Low uncentered R² indicating poor model fit when intercept is not considered.

---

## 📊 Key Insights

* **Interest Rate** positively impacts the Index Price.
* **Unemployment Rate** negatively impacts the Index Price.
* The model performs moderately well on the test data with \~76% variance explained.
* However, the **OLS model summary** shows that the model may not generalize well without more data or feature refinement.

---

## 📌 Things to Improve

* Add more **features** (e.g., inflation, GDP growth) to improve performance.
* Use **polynomial or interaction terms** if relationships are non-linear.
* Address possible **multicollinearity**.
* Include **lag variables** for temporal dynamics.

---

## ✅ Conclusion

This notebook demonstrates a classic application of **Multiple Linear Regression** using real-world economic indicators. It combines end-to-end steps: from data cleaning to training, validation, and residual diagnostics — offering a solid base for more advanced modeling.

---

## 🧪 Summary

Multiple Linear Regression is a foundational model in both statistics and machine learning. While it is relatively simple, it provides **powerful insights** into the relationships between multiple variables and the outcome. It also serves as a **baseline** for many advanced models.

---
