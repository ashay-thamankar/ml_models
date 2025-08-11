# 🌳 Decision Tree Algorithms – Classifier & Regressor

---

## 📌 About Decision Trees

A **Decision Tree** is a **supervised learning algorithm** used for both **classification** and **regression** tasks.
It works by **recursively splitting** the dataset based on feature values, creating a flowchart-like structure with:

* **Root Node** → starting point with all data.
* **Decision Nodes** → intermediate points where data is split based on feature conditions.
* **Leaf Nodes** → final predictions (class labels for classification, numerical values for regression).

**Key Idea:**
Find the feature and split that best separates the target variable by reducing impurity (for classification) or variance (for regression).

---

## 📊 How Decision Tree **Regressor** Works

1. **Starting Point**

   * All training samples start at the root node.

2. **Splitting Criterion**

   * For regression, the goal is to minimize **variance** in target values.
   * Common impurity metrics:

     * **Mean Squared Error (MSE):**

       $$
       MSE(t) = \frac{1}{N_t} \sum_{i=1}^{N_t} (y_i - \bar{y_t})^2
       $$

       where:
       $N_t$ = number of samples in node $t$
       $\bar{y_t}$ = mean target value in node $t$
     * **Mean Absolute Error (MAE):**

       $$
       MAE(t) = \frac{1}{N_t} \sum_{i=1}^{N_t} |y_i - \bar{y_t}|
       $$

3. **Best Split Selection**

   * For each feature $X_j$, consider all possible split thresholds $s$.
   * Compute impurity for left ($t_L$) and right ($t_R$) child nodes:

     $$
     \Delta I = I(t) - \left( \frac{N_{t_L}}{N_t} I(t_L) + \frac{N_{t_R}}{N_t} I(t_R) \right)
     $$
   * Choose the split with the **largest impurity decrease** $\Delta I$.

4. **Recursive Partitioning**

   * Repeat the process for each child node until stopping criteria are met.

5. **Prediction**

   * The predicted value for a leaf node is:

     $$
     \hat{y} = \frac{1}{N_t} \sum_{i=1}^{N_t} y_i
     $$

---

## 📊 How Decision Tree **Classifier** Works

1. **Starting Point**

   * All training samples start at the root node.

2. **Splitting Criterion**

   * The goal is to maximize **purity** (reduce impurity) of child nodes.
   * Common impurity metrics:

     **(a) Gini Impurity**

     $$
     Gini(t) = 1 - \sum_{k=1}^{K} p_k^2
     $$

     where $p_k$ = proportion of class $k$ samples in node $t$.

     **(b) Entropy** (Information Gain)

     $$
     Entropy(t) = - \sum_{k=1}^{K} p_k \log_2(p_k)
     $$

     Information Gain:

     $$
     IG = Entropy(t) - \left( \frac{N_{t_L}}{N_t} Entropy(t_L) + \frac{N_{t_R}}{N_t} Entropy(t_R) \right)
     $$

3. **Best Split Selection**

   * Choose the feature & threshold that maximizes Information Gain or minimizes Gini.

4. **Recursive Partitioning**

   * Continue splitting until:

     * All samples in a node belong to one class.
     * The maximum depth is reached.
     * Minimum samples per split criterion is met.

5. **Prediction**

   * Assign the **majority class** in the leaf node as the predicted label.

---

## 📐 Mathematical Intuition

Both Decision Tree Classifier and Regressor rely on **recursive binary partitioning**:

* At each node $t$, for each feature $X_j$ and each threshold $s$, compute the impurity reduction:

  $$
  \Delta I = I(t) - \left( \frac{N_{t_L}}{N_t} I(t_L) + \frac{N_{t_R}}{N_t} I(t_R) \right)
  $$
* Select the split with the **largest $\Delta I$**.
* Repeat until a stopping condition is met.

---

## ✂️ Pruning (Avoiding Overfitting)

Decision Trees are **prone to overfitting** if grown too deep. Pruning helps reduce complexity:

1. **Pre-pruning (Early Stopping)**

   * Limit **max\_depth**
   * Set **min\_samples\_split** or **min\_samples\_leaf**
   * Set **max\_features** considered at each split

2. **Post-pruning (Cost Complexity Pruning)**

   * Grow a full tree.
   * Remove branches that provide minimal gain in validation accuracy.
   * Use **Complexity Parameter (α)** to balance tree size vs. accuracy.

---

## ✅ Advantages

* Easy to interpret & visualize 📊
* Handles both numerical & categorical data
* No need for feature scaling
* Captures non-linear relationships naturally
* Can handle multi-output problems

---

## ⚠️ Limitations

* Prone to **overfitting** without pruning
* Sensitive to small changes in data (high variance)
* Greedy splitting → may not find globally optimal tree
* Can be biased towards features with more split points

---

## 📌 Applications

**Decision Tree Classifier**

* 📧 Spam email detection
* 🏥 Medical diagnosis
* 💳 Credit risk assessment
* 🛡️ Fraud detection

**Decision Tree Regressor**

* 🏠 Real estate price prediction
* 📈 Stock price trend modeling
* ⚡ Energy demand forecasting
* 📦 Sales and demand prediction

---
