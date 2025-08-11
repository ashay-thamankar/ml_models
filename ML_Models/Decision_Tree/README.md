# 🌳 Decision Tree Algorithms – Classifier & Regressor

---

## 📌 About Decision Trees

Decision Trees are **supervised learning algorithms** used for both **classification** and **regression**.
They work by splitting the dataset into smaller and smaller subsets based on feature values, creating a tree-like structure.
At the leaves, a predicted value (for regression) or class (for classification) is assigned.
They are **interpretable**, **non-parametric**, and can capture **non-linear relationships**.

---

## 🔍 How Decision Tree **Regressor** Works

1. **Root Node Creation**

   * Start with the entire dataset.

2. **Splitting Criterion**

   * For regression, splits are chosen to **minimize variance** in the target variable.
   * Common metrics: **Mean Squared Error (MSE)** or **Mean Absolute Error (MAE)**.

     * `MSE = (1/N) * Σ (y_i - y_mean)²`
       where `y_mean` is the average target value in the node.

3. **Recursive Splitting**

   * The dataset is split repeatedly into child nodes until stopping criteria are met (max depth, min samples, or minimal error reduction).

4. **Prediction**

   * At a leaf, the predicted value is the **average** of all target values in that node.

---

## 🔍 How Decision Tree **Classifier** Works

1. **Root Node Creation**

   * Start with all training data in one node.

2. **Splitting Criterion**

   * Splits are chosen to **maximize class purity**.
   * Common metrics:

     * **Gini Impurity**: `Gini = 1 - Σ (p_k)²`
       where `p_k` = proportion of samples of class `k` in the node.
     * **Entropy**: `Entropy = - Σ (p_k * log₂(p_k))`

3. **Recursive Splitting**

   * Continue splitting until nodes are pure or stopping criteria are met.

4. **Prediction**

   * The predicted class for a leaf node is the **majority class** of samples in that node.

---

## 📐 Mathematical Intuition

* **Regressor Objective** → Reduce target variance after each split.
* **Classifier Objective** → Reduce impurity (Gini or Entropy).
* At each node:

  1. Evaluate all possible feature thresholds.
  2. Calculate impurity (classification) or variance (regression) for each.
  3. Choose the split that gives the **largest reduction** in impurity or variance.

---

## ✂️ Pruning (Avoiding Overfitting)

Decision trees can become too deep and **overfit** the data.
**Pruning** helps simplify the model:

* **Pre-pruning (Early Stopping)**: Limit depth, set minimum samples per split, or require a minimum impurity decrease.
* **Post-pruning**: Grow the tree fully, then remove branches that do not improve validation performance.

---

## ✅ Advantages

* Easy to visualize & interpret
* Handles both numerical & categorical data
* No need for feature scaling
* Captures non-linear patterns

---

## ⚠️ Limitations

* Prone to **overfitting** without pruning
* High variance: small changes in data can change the tree
* Greedy splitting may not yield the globally optimal tree

---

## 📌 Applications

* **Decision Tree Classifier**:

  * Medical diagnosis
  * Spam detection
  * Fraud detection
  * Credit risk assessment

* **Decision Tree Regressor**:

  * Price prediction (houses, cars, products)
  * Demand forecasting
  * Risk assessment
  * Energy consumption prediction

---

### 1️⃣ Decision Tree Regressor – **Diabetes Prediction**

**Notebook:** [Decision\_Tree\_Regressor\_Example.ipynb](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Decision_Tree/Decision_Tree_Regressor_Example.ipynb)

* **Dataset:** Diabetes dataset from `sklearn.datasets`.
* **Goal:** Predict disease progression based on medical attributes like BMI, blood pressure, and serum measurements.
* **Process:**

  1. Data loaded and visualized with correlation heatmaps.
  2. Train/test split applied.
  3. Grid Search used to tune hyperparameters (`criterion`, `splitter`, `max_depth`, `max_features`).
  4. Model evaluated using **R² score**, **Mean Absolute Error (MAE)**, and **Mean Squared Error (MSE)**.
  5. Final optimized tree visualized.
* **Key Insight:** Proper parameter tuning improved performance and prevented overfitting.

---

### 2️⃣ Decision Tree Classifier – **Iris Flower Classification**

**Notebook:** [Decision\_Tree\_Classifier\_Example.ipynb](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Decision_Tree/Decision_Tree_Classifier_Example.ipynb)

* **Dataset:** Iris dataset from `sklearn.datasets`.
* **Goal:** Classify flowers into species (`Setosa`, `Versicolor`, `Virginica`) based on sepal and petal dimensions.
* **Process:**

  1. Dataset split into training and testing sets.
  2. Decision Tree Classifier trained and visualized.
  3. Grid Search applied to optimize `criterion`, `splitter`, `max_depth`, and `max_features`.
  4. Model evaluated using **accuracy**, **confusion matrix**, and **classification report**.
* **Key Insight:** Hyperparameter tuning achieved **\~93% accuracy**, with perfect classification for `Setosa` and strong performance on other classes.

---

