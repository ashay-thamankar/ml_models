# Elastic Net Regression 📘📈📎

## 📌 About Elastic Net

Elastic Net is a **regularized regression method** that linearly combines both **L1 (Lasso)** and **L2 (Ridge)** penalties. It was introduced to overcome the limitations of Lasso and Ridge when applied individually. Elastic Net is particularly effective when dealing with **high-dimensional data** (more features than observations), or when features are **highly correlated**.

It aims to improve model **generalization**, **reduce overfitting**, and **enhance feature selection** capabilities by leveraging the strengths of both regularization techniques.

---

## 🔍 Mathematical Formulation

The **objective function** for Elastic Net regression is:

$$
\text{Loss} = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 + \lambda_1 \sum_{j=1}^{p} |\beta_j| + \lambda_2 \sum_{j=1}^{p} \beta_j^2
$$

Where:

* $y_i$: Actual target value
* $\hat{y}_i$: Predicted target value
* $\beta_j$: Coefficient of the j-th feature
* $\lambda_1$: Regularization strength for L1 (Lasso)
* $\lambda_2$: Regularization strength for L2 (Ridge)

Alternatively, Elastic Net is often expressed using a **mixing parameter** $\alpha \in [0, 1]$:

$$
\text{Loss} = \sum_{i=1}^{n} (y_i - \hat{y}_i)^2 + \lambda \left[ \alpha \sum_{j=1}^{p} |\beta_j| + (1 - \alpha) \sum_{j=1}^{p} \beta_j^2 \right]
$$

Where:

* $\alpha = 1$: Pure Lasso
* $\alpha = 0$: Pure Ridge
* $0 < \alpha < 1$: Elastic Net
* $\lambda$: Overall strength of regularization

## 🔍 Mathematical Formulation

The **objective function** for Elastic Net regression is:

```

Loss = ∑(yᵢ - ŷᵢ)² + λ₁ ∑|βⱼ| + λ₂ ∑βⱼ²

```

Where:

- yᵢ: Actual target value  
- ŷᵢ: Predicted target value  
- βⱼ: Coefficient of the j-th feature  
- λ₁: Regularization strength for L1 (Lasso)  
- λ₂: Regularization strength for L2 (Ridge)  

Alternatively, Elastic Net is often expressed using a **mixing parameter** α ∈ [0, 1]:

```

Loss = ∑(yᵢ - ŷᵢ)² + λ \[ α ∑|βⱼ| + (1 - α) ∑βⱼ² ]

```

Where:

- α = 1 → Pure Lasso  
- α = 0 → Pure Ridge  
- 0 < α < 1 → Elastic Net  
- λ: Overall strength of regularization  
```

**Intuition:**

* The **L1 term** encourages sparsity (feature selection)
* The **L2 term** stabilizes the solution when features are correlated

---

## ⚙️ How Elastic Net Works

1. **Starts with linear regression** as the baseline.
2. Adds **L1 regularization**, which forces some coefficients to zero — useful for feature selection.
3. Adds **L2 regularization**, which shrinks all coefficients towards zero — useful for handling multicollinearity.
4. The **mixing parameter $\alpha$** controls the contribution of L1 and L2 penalties.
5. The model is trained to find the optimal balance between fitting the data and keeping the model simple/generalized.

---

## ✅ Advantages

* **Handles multicollinearity** well due to the L2 penalty.
* **Performs feature selection** using the L1 penalty.
* **Balances complexity and accuracy** effectively through the mixing parameter $\alpha$.
* **Useful for high-dimensional datasets** where $p > n$ (more features than samples).
* Reduces **overfitting** by penalizing large coefficients.

---

## ❌ Limitations

* **Hyperparameter tuning** (λ and α) is essential and computationally expensive.
* May **over-penalize** if regularization parameters are not chosen correctly.
* Interpretation of coefficients is harder compared to standard linear regression.
* Does not perform well if **true model is highly non-linear** unless combined with feature transformations.

---

## 🚀 Applications

Elastic Net is widely used in domains where **both feature selection and generalization** are critical:

* **Genomics / Bioinformatics**
  Selecting relevant genes from thousands of predictors.

* **Finance**
  Building predictive models with correlated economic indicators.

* **Marketing / Customer Analytics**
  Identifying influential customer attributes while avoiding overfitting.

* **Healthcare**
  Risk prediction using correlated medical metrics.

* **Sensor and IoT data**
  Modeling from high-dimensional time series or sensor inputs.

---

## 🛠️ When to Use Elastic Net

* When you have **many features** and expect **only a few to be important**.
* When features are **correlated**, which makes Lasso unstable.
* When you want a **balance** between **feature selection** and **model robustness**.
* When you want to **combine the strengths** of Lasso and Ridge.

---

# 🔗 Elastic Net Regression - Applied on Algerian Forest Fire Dataset

### Overview

This notebook showcases the **Elastic Net Regression** model in action, using the **Algerian Forest Fire dataset**. The objective is to predict the **Fire Weather Index (FWI)** based on various environmental and fire-related features. It walks through key steps such as data preprocessing, feature analysis, scaling, and model evaluation — emphasizing the strengths of Elastic Net.
You can explore the full notebook here: [Elastic Net Example Notebook](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Elastic_Net_Regression/Elastic_Net_Example.ipynb)

---

## 🧠 What This Notebook Covers

* Loading and preprocessing of real-world environmental data
* Handling class labels and encoding for binary classification
* Feature correlation analysis and multicollinearity detection
* Feature scaling using StandardScaler
* Training and comparing models: **Linear Regression**, **Lasso**, **Ridge**, and **Elastic Net**
* Evaluation using **R² Score** and **Mean Absolute Error**
* Use of **cross-validation** for hyperparameter tuning with ElasticNetCV

---

## 🔍 Focus: Elastic Net Regression

Elastic Net is a hybrid of **Lasso** and **Ridge** regression. It combines both **L1 (absolute)** and **L2 (squared)** penalty terms to improve predictive performance, especially in datasets with **high multicollinearity** or **many features**.

In this notebook:

* **ElasticNet** is trained and evaluated on scaled features.
* **ElasticNetCV** is used for tuning the optimal alpha and l1\_ratio.
* Its performance is compared with other linear models for interpretability.

---

