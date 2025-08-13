# Random Forest — Regressor & Classifier

Random Forest is an **ensemble** of decision trees built with two sources of randomness:
(1) **Bootstrap sampling** of the training data for each tree (bagging), and
(2) **Random feature subsetting** at each split.
The ensemble prediction is made by **averaging** (regression) or **majority vote** (classification). This reduces variance, improves generalization, and handles complex, non-linear relationships with minimal tuning.

---

## 🌲 Random Forest **Regressor**

### About

A Random Forest Regressor predicts a **continuous** target by averaging the outputs of many decision trees trained on different bootstrap samples and random subsets of features. It is robust to noise, scales to many features, and usually needs little preprocessing (no scaling/standardization required).

### How It Works

1. **Bootstrap (Bagging):** For each tree, sample the training set **with replacement** to create a bootstrap dataset of the same size.
2. **Grow a Tree:**

   * At each split, consider only a **random subset of features** (e.g., `max_features ≈ p/3` is a common heuristic).
   * Choose the split that most reduces **squared error** (node variance).
   * Grow until stopping criteria (e.g., `max_depth`, `min_samples_leaf`) are met.
3. **Out-of-Bag (OOB) Evaluation:** For each tree, about \~36.8% of samples are **not** in its bootstrap set; these **OOB samples** can estimate prediction error without a separate validation set.
4. **Ensemble Prediction:** For a new input `x`, collect predictions from all trees and **average** them:

   ```
   ŷ(x) = (1/T) * Σ_{t=1..T} h_t(x)
   ```

   where `h_t` is the t-th tree and `T` is the number of trees.

### Mathematical Intuition (Regression)

* **Split Criterion (Variance/MSE reduction):** At a node with samples `{y_i}`, the impurity is the mean squared deviation from the node mean:

  ```
  MSE(node) = (1/n) * Σ (y_i - ȳ)^2
  ```

  A split is chosen to **maximize impurity decrease**:

  ```
  Δ = MSE(parent) - [ (n_L/n) * MSE(left) + (n_R/n) * MSE(right) ]
  ```
* **Variance Reduction via Ensembling:** If each tree has variance `σ²` and average pairwise correlation `ρ`, then the variance of the forest average is:

  ```
  Var(Ŷ) ≈ σ² * [ ρ + (1 - ρ)/T ]
  ```

  → Increasing `T` lowers variance; reducing **correlation** between trees (via feature randomness) is equally crucial.

### Advantages

* **Strong accuracy** out-of-the-box; handles **non-linear** patterns and interactions.
* **Low variance** vs. single trees; **robust** to overfitting.
* Works well with **mixed feature types**; minimal preprocessing.
* **OOB error** provides a built-in generalization estimate.
* **Feature importance** offers interpretability signals (MDI and permutation importance).

### Limitations

* **Less interpretable** than a single tree.
* **Computationally heavier** at prediction time (many trees).
* Can struggle with **extrapolation** (predictions tend to stay within the training target range).
* **Feature importance bias** toward high-cardinality or noisy features (use permutation importance to mitigate).
* Not ideal for **very high-dimensional sparse** problems (linear models may outperform).

### Applications

* Price/score forecasting (e.g., **housing**, **insurance**, **credit risk**).
* **Demand** and **sales** prediction.
* **Environmental** and **time-series** regression (with tabular features).
* **Healthcare** risk and outcome scoring (continuous endpoints).

---

## 🌲 Random Forest **Classifier**

### About

A Random Forest Classifier predicts a **categorical** label via the **majority vote** of many randomized decision trees. It is robust to noise, handles non-linear class boundaries, and typically delivers strong accuracy with little tuning.

### How It Works

1. **Bootstrap (Bagging):** Build each tree on a bootstrap sample of the training set.
2. **Random Subspace at Splits:** At each node, evaluate a **random subset of features** (common heuristic: `max_features ≈ sqrt(p)`).
3. **Split Criterion (Impurity):** Choose the split that most reduces impurity (e.g., **Gini** or **Entropy**).
4. **Vote & Probabilities:** For a new `x`, each tree predicts a class `h_t(x)`. The forest predicts:

   ```
   P̂(y = c | x) = (1/T) * Σ_{t=1..T} 1[h_t(x) = c]
   ŷ(x) = argmax_c P̂(y = c | x)
   ```
5. **OOB Error (Optional):** Use trees that did not see each sample to estimate generalization accuracy without a held-out set.

### Mathematical Intuition (Classification)

* **Impurity Measures:**

  * **Gini:** `G = 1 - Σ_k p_k^2`
  * **Entropy:** `H = - Σ_k p_k * log2(p_k)`
    (where `p_k` is the class proportion in the node)
    Choose the split that **maximizes impurity reduction** (information gain).
* **Ensemble Effect:** As with regression, averaging **correlated** base learners reduces variance. Random feature selection at splits lowers correlation, improving generalization.

### Advantages

* **High accuracy** with strong generalization.
* **Robust to overfitting** and to outliers.
* Handles **multiclass** and **mixed-type** features.
* **Built-in probability estimates** from vote fractions.
* **Permutation importance** helps identify influential features.

### Limitations

* **Lower interpretability** vs. a single tree; model size can be large.
* **Slower inference** for real-time constraints.
* Can be **biased** with highly imbalanced classes (use class weights, resampling).
* Importance can be **biased** toward high-cardinality categorical features (prefer permutation importance).
* Not optimal for **very sparse high-dimensional** problems (linear or tree-boosting may do better).

### Applications

* **Fraud** and **anomaly** detection.
* **Churn** prediction, **customer segmentation**, **propensity** modeling.
* **Medical** and **bioinformatics** classification (diagnosis, risk stratification).
* **Document/text** classification (with engineered tabular features).
* **Quality control** and **fault detection** in manufacturing.

---

### Practical Notes (useful for both)

* Typical defaults work well; tune **`n_estimators`, `max_depth`, `min_samples_leaf`, `max_features`, `bootstrap`**.
* Use **OOB error** for quick validation when data is limited.
* Prefer **permutation importance** over Gini/MDI for more reliable feature importance.
* Handle **imbalance** with `class_weight`, resampling, or appropriate metrics (AUC, F1).
* RFs don’t require scaling, but **duplicates/leakage** and **target leakage** must be avoided for fair evaluation.

---

# Random Forest Regression on CarDekho Dataset

This project demonstrates the application of various regression models, with a focus on **Random Forest Regressor**, to predict car selling prices using the CarDekho dataset.

## Repository Link

[Random Forest Regression Example Notebook](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Random_Forest/Random_Forest_Regression_Example.ipynb)

## Project Overview

The notebook walks through:

* Loading and exploring the dataset (`cardekho_imputated.csv`)
* Data cleaning:

  * Handling missing values and duplicates
  * Removing irrelevant columns (`car_name`, `brand`)
  * Identifying numerical, categorical, discrete, and continuous features
* Feature engineering:

  * Label Encoding for high-cardinality categorical columns
  * One-Hot Encoding for low-cardinality categorical columns
  * Standard scaling for numerical features
* Splitting data into training and testing sets

## Model Training & Evaluation

Multiple regression models were trained and evaluated:

* Linear Regression
* Lasso & Ridge Regression
* K-Neighbors Regressor
* Decision Tree Regressor
* Random Forest Regressor

Evaluation metrics:

* Root Mean Squared Error (RMSE)
* Mean Absolute Error (MAE)
* R² Score

## Hyperparameter Tuning

* **KNN** and **Random Forest** models were tuned using `RandomizedSearchCV`
* Best parameters for Random Forest:

  * `n_estimators = 500`
  * `max_depth = 15`
  * `max_features = 5`
  * `min_samples_split = 2`
* Final Random Forest Model achieved:

  * **R² Score:** 0.9416 on test set

## Key Insights

* Random Forest outperformed other models with high accuracy and low error metrics.
* Feature encoding and scaling significantly improved model performance.
* Hyperparameter tuning provided notable gains in prediction quality.

---

# Random Forest Classifier – Travel Dataset

This project demonstrates building a **Random Forest Classifier** model to predict whether a customer purchased a travel package (`ProdTaken`) based on demographic, behavioral, and engagement-related features.

## Notebook Link

You can view the complete implementation here:
[Random Forest Classifier Example – GitHub](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Random_Forest/Random_Forest_Classification_Example.ipynb)

## Dataset

The dataset (`Travel.csv`) contains customer details such as:

* Demographics (Age, Gender, Marital Status, Occupation)
* Contact details (Type of Contact, City Tier)
* Travel-related attributes (Duration of Pitch, Number of Trips, Product Pitched)
* Lifestyle & assets (Own Car, Passport)
* Financial data (Monthly Income)

## Workflow Overview

1. **Data Loading & Exploration**

   * Imported required libraries
   * Loaded dataset and examined structure, data types, and missing values

2. **Data Cleaning**

   * Fixed inconsistent categories (e.g., `"Fe Male"` → `"Female"`)
   * Handled missing values using median or mode imputation
   * Removed unnecessary columns (e.g., `CustomerID`)

3. **Feature Engineering**

   * Created `TotalVisiting` from `NumberOfPersonVisiting` + `NumberOfChildrenVisiting`
   * Categorized features into numerical, categorical, discrete, and continuous

4. **Data Preprocessing**

   * Applied **One-Hot Encoding** for categorical features
   * Applied **Standard Scaling** for numerical features
   * Used `ColumnTransformer` to combine preprocessing steps

5. **Model Training**

   * Split data into **Train (80%)** and **Test (20%)**
   * Trained **Random Forest Classifier** on processed features
   * Evaluated model performance on test data

6. **Applications**

   * Predict travel package purchase likelihood
   * Help travel companies in targeted marketing

---
