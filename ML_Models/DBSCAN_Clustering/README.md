# 📌 DBSCAN Clustering Algorithm

## 📖 About

**DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** is an **unsupervised clustering algorithm** widely used in data mining and machine learning. Unlike partitioning methods like *k-means*, DBSCAN groups together points that are **closely packed (dense regions)** and marks points that lie alone in low-density regions as **outliers (noise)**.

The main idea is:

* A cluster is formed if there are enough points (**MinPts**) within a given distance (**ε, epsilon**) of each other.
* It is powerful for discovering **arbitrarily shaped clusters** (not just circular/convex).
* It is also robust to noise/outliers, making it well-suited for **real-world messy data**.

---

## ⚙️ How it Works

DBSCAN defines clusters based on **density connectivity**:

1. **Core Point**

   * A point is a *core point* if at least **MinPts** points are within its **ε-neighborhood**.

2. **Directly Density-Reachable**

   * A point `q` is directly density-reachable from `p` if `q` lies within ε distance of `p` and `p` is a core point.

3. **Density-Reachable**

   * A chain of directly density-reachable points makes one density-reachable from another.

4. **Border Point**

   * A point that is not a core point but lies within the neighborhood of a core point.

5. **Noise (Outlier)**

   * A point that is neither a core point nor reachable from any core point.

### 🧮 Mathematical Intuition

For a dataset with points `x₁, x₂, …, xₙ`:

* Define the **ε-neighborhood** of a point `xᵢ`:

  ```
  Nε(xᵢ) = { xⱼ ∈ D | dist(xᵢ, xⱼ) ≤ ε }
  ```
* If `|Nε(xᵢ)| ≥ MinPts`, then `xᵢ` is a **core point**.
* Clusters are formed by connecting density-reachable core points.
* Outliers are defined as:

  ```
  Noise = { x ∈ D | x is not density-reachable from any core point }
  ```

Thus, DBSCAN uses **density-based connectivity** instead of a global objective function (like k-means).

---

## 🌟 Advantages

* ✅ Can discover **arbitrarily shaped clusters** (not just spherical).
* ✅ No need to pre-specify the number of clusters (unlike k-means).
* ✅ Automatically detects **outliers/noise**.
* ✅ Works well with clusters of different sizes and shapes.
* ✅ More robust compared to centroid-based methods.

---

## ⚠️ Limitations

* ⏳ Computationally expensive on large, high-dimensional datasets.
* ❌ Struggles when clusters have **varying densities**.
* ❌ Sensitive to parameters **ε** and **MinPts**.
* ❌ Not ideal for very high-dimensional data (distance metrics lose meaning).

---

## 🚀 Applications

* 🌍 **Geospatial data**: Detecting hotspots (e.g., crime, disease spread).
* 🛰️ **Image segmentation**: Identifying objects in images.
* 🛍️ **Market segmentation**: Grouping customers with irregular buying patterns.
* 📡 **Anomaly detection**: Fraud detection, network intrusion detection.
* 📊 **Scientific research**: Finding patterns in astronomy, biology, etc.

---

✨ DBSCAN is a **powerful density-based clustering algorithm** that shines in detecting clusters of arbitrary shapes and handling noise, but requires careful parameter tuning.

---

# DBSCAN Clustering Example 🚀

This repository contains a simple implementation of the **DBSCAN (Density-Based Spatial Clustering of Applications with Noise)** algorithm using the `scikit-learn` library.

The notebook demonstrates how DBSCAN works on a synthetic **two-moon dataset**, showcasing how it identifies clusters based on density rather than distance alone.

🔗 **Notebook Link**:
[DBSCAN Clustering Example](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/DBSCAN_Clustering/DBSCAN_Clustering_Example.ipynb)

📌 **Key Highlights**:

* Generates a non-linear "two-moons" dataset.
* Applies feature scaling for better performance.
* Fits the **DBSCAN model** with defined parameters (`eps`, `min_samples`).
* Visualizes clustering results with `matplotlib`.

---
