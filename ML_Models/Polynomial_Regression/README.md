# 📘 Polynomial Regression – Mathematical Foundations & Interpretation

## 🔍 What is Polynomial Regression?

Polynomial Regression is a type of **regression analysis** in which the relationship between the independent variable `x` and the dependent variable `y` is modeled as an **nth-degree polynomial**.

It is a form of **linear regression** where the **features are transformed**, but the model is still linear in terms of the parameters (coefficients).

---

## 📐 Mathematical Formulation

### ✅ General Equation

The general form of a polynomial regression model of degree `n` is:

```
y = β₀ + β₁x + β₂x² + β₃x³ + ... + βₙxⁿ + ε
```

Where:

* `y` = dependent variable
* `x` = independent variable
* `β₀, β₁, ..., βₙ` = model coefficients
* `ε` = error term (residual)

Despite the **non-linear curve** of the equation, it is considered a **linear model** because it is linear in its parameters (β’s).

---

## 🔄 How it Works

1. **Feature Transformation**:

   * The original input variable `x` is **expanded** into higher-order terms: `x²`, `x³`, ..., `xⁿ`.

2. **Linear Regression on Transformed Features**:

   * The transformed variables are treated as separate input features, and a standard linear regression is applied.

---

## 🧮 Matrix Representation

Given:

* X: the design matrix (with polynomial terms)
* β: vector of coefficients
* y: target variable

The model can be written as:

```
y = Xβ + ε
```

Where:

```
X = [1, x, x², ..., xⁿ]
```

This formulation allows us to solve for `β` using the **Normal Equation**:

```
β = (XᵗX)⁻¹Xᵗy
```

---

## 📈 Why Use Polynomial Regression?

* **Captures non-linear relationships** between variables.
* More flexible than linear regression while retaining interpretability.
* Particularly useful when the data shows a **curved trend** that cannot be captured by a straight line.

---

## 📌 Assumptions (same as Linear Regression)

Despite the polynomial terms, it still relies on linear regression assumptions:

1. **Linearity in parameters**: The model is linear in β.
2. **Homoscedasticity**: Constant variance of residuals.
3. **Independence**: Observations are independent.
4. **Normality of errors**: Residuals are normally distributed.
5. **Low multicollinearity**: Especially relevant as powers of `x` can be highly correlated.

---

## 📊 Model Evaluation Metrics

* **R² (Coefficient of Determination)** – Measures the proportion of variance explained.
* **Adjusted R²** – Penalizes addition of unnecessary higher-order terms.
* **MSE / RMSE / MAE** – Standard error metrics.
* **Residual Plots** – Check for randomness of errors.
* **Cross-Validation** – To prevent overfitting.

---

## ⚠️ Common Pitfalls

* **Overfitting**:

  * Higher-degree polynomials may fit the training data too well and generalize poorly.

* **Multicollinearity**:

  * Powers of `x` can become strongly correlated (e.g., `x` vs. `x²`), leading to instability in coefficient estimates.

* **Extrapolation Risk**:

  * Polynomial models are unreliable outside the range of training data due to extreme curvature.

---

## 🧠 Bias-Variance Tradeoff

* **Low-degree polynomial**: May underfit the data → High bias, low variance.
* **High-degree polynomial**: May overfit the data → Low bias, high variance.

Choosing the **right degree** involves **cross-validation** and understanding the data’s structure.

---

## ✅ When to Use Polynomial Regression

* You suspect or observe a **curved relationship** between `x` and `y`.
* Residual plots from linear regression indicate **non-random patterns**.
* You want a **simple, interpretable** model compared to more complex non-linear models like SVR, trees, or neural networks.

---

## 🧩 Alternatives to Polynomial Regression

* **Spline Regression** – Piecewise polynomial fitting.
* **Generalized Additive Models (GAMs)** – Combine flexibility of splines with additive structure.
* **Decision Trees / Random Forests** – Non-parametric models that capture non-linearity.
* **Support Vector Regression (SVR)** – Works well for non-linear regression.

---

## 📝 Summary

* Polynomial Regression is a **powerful extension** of linear regression.
* It enables us to fit **non-linear patterns** by transforming input features.
* While easy to implement, it must be used **cautiously** to avoid overfitting and multicollinearity.
* Always validate using **cross-validation** and interpret results using residuals and performance metrics.

# 🧪 Polynomial Regression – Practical Implementation

## 📊 Step 1: Dataset Creation

* A dataset is synthetically generated with 100 samples, where `X` values are randomly drawn from a uniform distribution between `-3` and `+3`.

* The target variable `y` is generated using a **second-degree polynomial equation**:

  ```
  y = 0.5x² + 1.5x + 2 + noise
  ```

* Random noise is added using a standard normal distribution to simulate real-world data imperfections.

---

## 🔀 Step 2: Train-Test Split

* The data is split into training (80%) and testing (20%) sets.
* This allows evaluation of model performance on unseen data and avoids overfitting.

---

## 📈 Step 3: Linear Regression (Baseline)

* A **Simple Linear Regression** model is trained on the training data.
* Since the true relationship is quadratic, a straight-line model won't fully capture the curve.
* The **R² score** on the test data shows the model explains only a portion of the variance.
* A visual plot confirms the poor fit: the straight line does not follow the curved trend in the data.

---

## 📉 Step 4: Polynomial Regression (Degree = 2)

* The input features are transformed using **PolynomialFeatures** with degree 2.
* This adds `x²` as a new feature, enabling the model to capture the quadratic nature.
* A new **Linear Regression** is trained on the transformed features.
* The **R² score significantly improves**, indicating a much better fit to the test data.
* The model coefficients show that:

  * `β₀ ≈ 1.96` (intercept)
  * `β₁ ≈ 1.51` (linear term)
  * `β₂ ≈ 0.48` (quadratic term)
* This aligns closely with the true data-generating equation.

---

## 🔁 Step 5: Polynomial Regression (Degree = 3)

* To explore whether a **higher-degree** polynomial performs better, the degree is increased to 3.
* The third-degree term (`x³`) is added as a feature.
* The **R² score is slightly lower** than degree 2, suggesting possible **overfitting**.
* This illustrates the **bias-variance tradeoff**: higher complexity does not always improve generalization.

---

## 📊 Step 6: New Predictions & Visualization

* A new set of `X` values in the range `[-3, 3]` is generated.
* The trained polynomial model (degree 3) is used to make predictions.
* A line plot is drawn showing:

  * The polynomial regression prediction curve
  * The original training and test data points
* This visualization helps confirm how well the model captures the underlying trend.

---

## 🧰 Step 7: Using Pipelines for Simplification

* A **scikit-learn Pipeline** is introduced to streamline the workflow:

  * First step: `PolynomialFeatures` transformation
  * Second step: `LinearRegression` fitting
* The pipeline encapsulates both transformations and modeling into one object.
* A function is defined to generate and visualize models of varying polynomial degrees using this pipeline.
* The model with **degree 6** is plotted to observe how complexity increases curve fitting.

---

## 📌 Key Takeaways

* Polynomial Regression can accurately model **non-linear relationships** using linear algorithms.
* Model complexity (degree of the polynomial) should be chosen carefully to balance **fit vs generalization**.
* Pipelines make the modeling process **modular and reusable**, especially when combining multiple steps.
* Visualizations and R² scores provide insight into how well a model fits the data.

---

## 📎 Useful Concepts Covered

* Feature transformation using `PolynomialFeatures`
* Model training with `LinearRegression`
* Model evaluation using `r2_score`
* Data visualization using `matplotlib`
* Workflow automation using `Pipeline`

