# Local Outlier Factor (LOF)

## 📌 About

Local Outlier Factor (LOF) is an **unsupervised anomaly detection algorithm** that identifies data points which significantly deviate from their neighbors. Unlike global methods, LOF focuses on **local density deviation**, making it powerful for datasets with varying densities.

---

## ⚙️ How It Works

1. **Neighborhood Selection (k-nearest neighbors):**
   For each data point, LOF identifies its `k` nearest neighbors.

2. **Reachability Distance:**
   The distance of a point `A` to a neighbor `B` is defined as:

   ```
   reach-dist_k(A, B) = max{k-distance(B), d(A, B)}
   ```

   where `k-distance(B)` is the distance of `B` to its k-th nearest neighbor, and `d(A,B)` is the actual distance.

3. **Local Reachability Density (LRD):**
   Measures how closely a point is surrounded by its neighbors:

   ```
   LRD_k(A) = 1 / (avg(reach-dist_k(A, B) for B in neighbors_k(A)))
   ```

4. **Local Outlier Factor (LOF):**
   The anomaly score is defined as the ratio of the average LRD of neighbors to the LRD of the point:

   ```
   LOF_k(A) = avg(LRD_k(B) / LRD_k(A) for B in neighbors_k(A))
   ```

   * If `LOF ≈ 1` → point has similar density to neighbors (normal).
   * If `LOF >> 1` → point has much lower density (outlier).

---

## 🔢 Mathematical Intuition

* LOF leverages **relative density** instead of absolute distance.
* Example analogy: A fish among other fish 🐟 is normal, but the same fish among birds 🐦 becomes an “outlier.”
* Formula-style intuition:

  ```
  LOF(xᵢ) ≈ ( Σ (LRD of neighbors) / (LRD of xᵢ) ) / k
  ```

  where low LRD means sparse neighborhood → high anomaly score.

---

## ✅ Advantages

* Captures **local density variations** 🔍.
* Handles datasets with **non-uniform distributions**.
* Works well for **unsupervised anomaly detection** (no labels needed).
* Provides **relative anomaly scores**.

---

## ❌ Limitations

* Sensitive to **parameter `k` (neighbors)**.
* Computationally expensive ⚡ on large datasets.
* Scores may vary with different contamination assumptions.
* Not ideal for **very high-dimensional data**.

---

## 🚀 Applications

* Fraud detection 💳
* Intrusion detection in cybersecurity 🔐
* Sensor fault detection ⚙️
* Outlier detection in manufacturing & supply chain 🏭
* Healthcare anomaly detection 🩺

---

## 📝 Example Usage

A **full working example** of LOF in Python (with synthetic dataset and visualization) is included in this repo:

👉 [Example Code – LOF Implementation](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Local_Outlier_Factor/example_lof.py)

This example demonstrates:

* Creating a toy dataset with inliers & outliers
* Fitting **LOF (unsupervised mode)**
* Visualizing outliers vs inliers

---
