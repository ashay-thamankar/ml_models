# 📊 K-Means Clustering

K-Means is one of the most popular **unsupervised machine learning algorithms** used for clustering.
It groups similar data points into **K clusters** by minimizing the distance between data points and their assigned cluster center (centroid).

---

## ⚙️ How It Works

1. Choose the number of clusters **K**.
2. Randomly initialize **K centroids**.
3. Assign each data point to the **nearest centroid** (using distance metrics like Euclidean distance).
4. Update centroids by calculating the **mean** of points assigned to each cluster.
5. Repeat steps 3–4 until convergence (centroids stop moving or max iterations reached).

---

## 🧮 Mathematical Intuition

K-Means minimizes the **Within-Cluster Sum of Squares (WCSS)**, also called **inertia**:

J = Σ (from i=1 to K) Σ (x ∈ Cᵢ) || x - μᵢ ||²

Where:

* **K** = number of clusters
* **x** = data point
* **Cᵢ** = cluster i
* **μᵢ** = centroid of cluster i
* **|| x - μᵢ ||²** = squared distance between data point and centroid

The algorithm seeks to minimize this cost function **J**, giving compact and well-separated clusters.

---

## ✨ Advantages

* **Simple & Fast** ⚡ – easy to understand and quick to run even on large datasets.
* **Scalable** 📈 – performs well with big data.
* **Efficient** 🎯 – works well when clusters are spherical and equally sized.
* **Interpretable** 🔍 – centroids make clusters easy to analyze.

---

## ⚠️ Limitations

* **Requires K** ❓ – you must pre-define the number of clusters.
* **Sensitive to Initialization** 🎲 – different starting points can lead to different results.
* **Assumes Equal Size** 📦 – struggles with clusters of varying density or size.
* **Affected by Outliers** 🚨 – a single outlier can distort centroids.

---

## 🌍 Applications

* **Customer Segmentation** 🛒 – group customers by behavior for targeted marketing.
* **Image Compression** 🖼️ – reduce colors by clustering pixel values.
* **Document Clustering** 📚 – organize news articles or research papers by similarity.
* **Anomaly Detection** 🔎 – detect unusual patterns by identifying points far from clusters.
* **Genomics & Healthcare** 🧬 – group patients by symptoms or genetic data.

---

✅ **In summary:**
K-Means is a **powerful, simple, and widely used clustering algorithm** that works best on well-separated, spherical clusters. While it has limitations (like sensitivity to K and outliers), it remains a go-to choice for many real-world applications.

---

## 📂 K-Means Clustering Notebook Examples

**[K-Means Example](https://github.com/ashay-thamankar/ml_models/tree/main/ML_Models/Kmeans_Clustering)**

* **Data Generation** → Synthetic blobs data created for testing.
* **Preprocessing** → Feature scaling using `StandardScaler`.
* **Modeling** → K-Means clustering with `k-means++` initialization.
* **Evaluation** → Elbow method & Silhouette score for K selection.
