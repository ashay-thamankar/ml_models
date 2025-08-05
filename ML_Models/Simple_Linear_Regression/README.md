# 📘 Linear Regression – Detailed Explanation

## 🔍 Overview

**Linear Regression** is one of the most fundamental and widely used statistical and machine learning algorithms. It models the relationship between a **dependent variable (target)** and one or more **independent variables (features)** by fitting a straight line (in higher dimensions, a hyperplane) to the data.

---

## 📈 Objective

To find the **best-fitting line** that minimizes the difference between the actual and predicted values of the dependent variable.

---

## 📐 Equation

### ➤ **Simple Linear Regression (One Independent Variable)**:

  **y = β₀ + β₁x + ε**

Where:

* **y** = Dependent variable (target)
* **x** = Independent variable (feature)
* **β₀** = Intercept (value of y when x = 0)
* **β₁** = Slope (change in y per unit change in x)
* **ε** = Error term (difference between actual and predicted)

### ➤ **Multiple Linear Regression (Multiple Features)**:

  **y = β₀ + β₁x₁ + β₂x₂ + ... + βₙxₙ + ε**

---

## ⚙️ How It Works

Linear regression finds the best coefficients (**β**) by **minimizing the error** between predicted and actual values. This is done using:

### ✔️ **Ordinary Least Squares (OLS)**

OLS minimizes the **sum of squared residuals**:
  **Loss Function**:
  **L = Σ(yᵢ - ŷᵢ)²**
Where:

* **yᵢ** = actual value
* **ŷᵢ** = predicted value
* **(yᵢ - ŷᵢ)** = residual/error

The model uses calculus (partial derivatives and gradient descent or matrix algebra) to find the optimal **β** values that minimize this loss.

---

## 📌 Assumptions of Linear Regression

1. **Linearity**: Relationship between dependent and independent variables is linear.
2. **Homoscedasticity**: Constant variance of errors across all levels of the independent variables.
3. **Independence**: Observations are independent of each other.
4. **No multicollinearity**: Independent variables are not highly correlated with each other.
5. **Normality of errors**: Errors (residuals) are normally distributed.

---

## 🧪 Evaluation Metrics

To assess model performance:

| Metric       | Description                                   |
| ------------ | --------------------------------------------- |
| **R² Score** | Proportion of variance explained by the model |
| **MAE**      | Mean Absolute Error                           |
| **MSE**      | Mean Squared Error                            |
| **RMSE**     | Root Mean Squared Error                       |

---

## ✅ Advantages

* Easy to understand and interpret
* Computationally efficient
* Requires fewer resources
* Serves as a good baseline model
* Works well with linearly separable data

---

## ⚠️ Limitations

* Assumes linear relationships
* Sensitive to outliers
* Prone to underfitting for complex data
* Cannot handle multicollinearity well (in multiple regression)
* Poor performance if assumptions are violated

---

## 🎯 Applications

* House price prediction
* Stock price trend estimation
* Salary prediction based on experience
* Demand forecasting
* Risk assessment in finance and insurance
* Medical cost estimation

---

## 📎 Example Use Case in Notebook

In this notebook:

* We import data and preprocess it
* Use `scikit-learn` to build a Linear Regression model
* Fit the model and interpret the coefficients
* Visualize the line of best fit
* Evaluate using R², MAE, and RMSE
* Discuss residual plots and assumption checks

---

## 🧪 Notebook Summary: Linear Regression Example

This notebook demonstrates **Simple Linear Regression** using a dataset of **Height vs. Weight**.

### 📋 Steps Covered:

1. **Data Loading & Visualization**

   * Loaded `height-weight.csv`
   * Created scatter plots to visualize the relationship
   * Found a strong positive correlation (0.93) between Weight and Height

2. **Data Preparation**

   * Defined Weight as the **independent variable (X)** and Height as the **dependent variable (y)**
   * Split the data into training and testing sets (75/25)
   * Standardized the input feature using `StandardScaler`

3. **Model Training**

   * Applied `LinearRegression()` from `sklearn`
   * Fitted the model on training data
   * Learned coefficients:

     * **Slope (β₁)**: \~17.29
     * **Intercept (β₀)**: \~156.47

4. **Model Evaluation**

   * Predicted values for test data
   * Calculated:

     * **MSE**: 114.84
     * **MAE**: 9.67
     * **RMSE**: 10.71
     * **R² Score**: 0.736
     * **Adjusted R²**: 0.67

5. **OLS (Statsmodels) Comparison**

   * Also fitted the model using `statsmodels.OLS`
   * Generated detailed statistical summary (p-values, t-stats, R², etc.)
   * Note: R² was low due to model fitted **without intercept**

6. **New Prediction**

   * Predicted Height for new Weight value (72 kg):
     ➤ **Predicted Height ≈ 155.98 cm**

---

### 🔍 Key Insight:

Linear Regression successfully captured the positive relationship between weight and height, showing good predictive power with a relatively high R² value.

---

## 📚 Conclusion

Linear Regression is a powerful yet simple algorithm for modeling relationships in data. While it’s easy to deploy and interpret, it’s essential to validate assumptions and understand its limitations. It's often the first step in understanding the structure of data before moving to more complex models.

---

