# K-Nearest Neighbors (KNN) — Classifier & Regressor

## 📌 About KNN

K-Nearest Neighbors (KNN) is a **non-parametric, instance-based learning algorithm** used for both classification and regression tasks.
It makes predictions by looking at the **K most similar training examples** (neighbors) to a new data point and using their information to determine the output.

* In **classification**, it assigns the majority class among the neighbors.
* In **regression**, it predicts the average (or weighted average) of the neighbors’ values.

KNN is intuitive, easy to implement, and works well when decision boundaries are irregular.

---

## ⚙️ How It Works

### 1. Choose **K**

* Select the number of neighbors (**K**).
* Small K → more sensitive to noise; Large K → smoother decision boundary.

### 2. Measure Distance

* Calculate distance between the new data point and all points in the training set.
* Common distance metrics:

  * **Euclidean Distance**:

    $$
    d(p, q) = \sqrt{\sum_{i=1}^n (p_i - q_i)^2}
    $$
  * **Manhattan Distance**:

    $$
    d(p, q) = Σ_{i=1}^n ∣p_i - q_i
    $$
  * Others: Minkowski, Cosine similarity.

### 3. Find Nearest Neighbors

* Select the **K points** with the smallest distances.

### 4. Make Prediction

* **Classifier**: Take a majority vote of the K neighbors’ classes.
* **Regressor**: Take the mean (or weighted mean) of neighbors’ target values.

---

## 📐 Mathematical Intuition

### **Classification**

Given:

* Query point $x$
* Training set $(x_1, y_1), (x_2, y_2), \dots, (x_m, y_m)$
* Distance function $d(\cdot, \cdot)$

**Steps:**

1. Compute distances: $d(x, x_i)$ for all training points.
2. Sort points by distance and pick **K** closest.
3. Predicted class:

   $$
   $\hat{y} = \arg\max_{c \in C} \sum_{i \in N_K(x)} I(y_i = c)$
   $$

   where $N_K(x)$ is the set of K nearest neighbors.

### **Regression**

For regression:

$$
\hat{y} = \frac{1}{K} \sum_{i \in N_K(x)} y_i
$$

For **weighted KNN regression** (closer neighbors have more influence):

$$
\hat{y} = \frac{\sum_{i \in N_K(x)} \frac{y_i}{d(x, x_i)}}{\sum_{i \in N_K(x)} \frac{1}{d(x, x_i)}}
$$

---

## 🌟 Advantages

* Simple and easy to implement.
* No training phase (lazy learning) — fast to set up.
* Works well with non-linear decision boundaries.
* Naturally handles multi-class classification.
* No assumptions about data distribution.

---

## ⚠️ Limitations

* **Computationally expensive** for large datasets (distance calculation for every query).
* **Memory intensive** (must store the entire dataset).
* Sensitive to **irrelevant features** and **feature scaling**.
* **Choice of K** is critical; too small → overfitting, too large → underfitting.
* Poor performance in high-dimensional data due to the **curse of dimensionality**.

---

## 🎯 Applications

* **Classification**:

  * Handwriting recognition (e.g., digit classification)
  * Image categorization
  * Medical diagnosis (based on symptoms similarity)
* **Regression**:

  * Predicting house prices based on similar properties
  * Forecasting product demand
  * Recommendation systems (based on user similarity)

---

## 📝 Summary

KNN is a **simple yet powerful** algorithm that leverages similarity between data points.
Its performance relies heavily on:

* Proper feature scaling (e.g., StandardScaler, MinMaxScaler)
* Optimal K selection
* Relevant feature selection

For smaller datasets with non-linear patterns, KNN can be a **great baseline** model before moving to more complex approaches.

---
