# 📄 Naive Bayes Classifier – Complete Guide

## 📌 About

Naive Bayes is a **probabilistic machine learning algorithm** based on **Bayes’ Theorem** with a strong (naive) assumption that all features are **independent** given the class label.
Despite this simplification, Naive Bayes often performs exceptionally well in text classification, spam filtering, sentiment analysis, and other domains.
It is **fast, simple, and effective** for large datasets, especially when feature independence holds approximately.

---

## ⚙️ How It Works

1. **Training Phase:**

   * Calculate the **prior probability** of each class from the training data.
   * Calculate the **likelihood** of each feature value given a class.
   * Store these probabilities for use during prediction.

2. **Prediction Phase:**

   * For a new data point, apply **Bayes’ Theorem** to compute the posterior probability for each class:

     $$
     P(Class | Features) \propto P(Class) \times \prod_{i=1}^{n} P(Feature_i | Class)
     $$
   * Assign the class with the **highest posterior probability**.

3. **Key Assumption:**

   * All features are **conditionally independent** given the class label (hence "naive").

---

## 📐 Mathematical Intuition

Bayes’ Theorem:

$$
P(C | X) = \frac{P(X | C) \cdot P(C)}{P(X)}
$$

Where:

* $P(C | X)$ → Posterior probability (class given features)
* $P(X | C)$ → Likelihood (features given class)
* $P(C)$ → Prior probability (class before seeing features)
* $P(X)$ → Evidence (probability of features across all classes)

**Naive Bayes Assumption:**

$$
P(X | C) = \prod_{i=1}^{n} P(X_i | C)
$$

This simplifies computation significantly.

---

## ✅ Advantages

* **Fast & Efficient:** Works well even with large datasets.
* **Performs well with small data:** Even with limited training examples.
* **Effective for Text Data:** Works great for bag-of-words models in NLP.
* **Simple to Implement:** Few parameters to tune.
* **Robust to Irrelevant Features:** Irrelevant features have less impact due to independence assumption.

---

## ⚠️ Limitations

* **Feature Independence Assumption:** Rarely holds true in real-world datasets.
* **Zero Probability Problem:** If a feature value is unseen in training, its probability becomes zero → handled using **Laplace smoothing**.
* **Continuous Variables:** Requires assuming a distribution (e.g., Gaussian) for continuous features.
* **Not Good for Highly Correlated Features:** Correlation between features violates independence assumption and reduces performance.

---

## 🎯 Applications

* **Spam Email Filtering** 📧
* **Sentiment Analysis** 😊😡
* **Document Categorization** 📚
* **Medical Diagnosis** 🩺
* **Recommendation Systems** 🎯

---

## 🧩 Types of Naive Bayes Algorithms

1. **Gaussian Naive Bayes**

   * Assumes continuous features follow a **Gaussian (Normal) distribution**.
   * Likelihood:

     $P(x_i \mid y) = \frac{1}{\sqrt{2\pi\sigma_y^2}} \exp\left( -\frac{(x_i - \mu_y)^2}{2\sigma_y^2} \right)$
     
   * Used for datasets with continuous numeric features.

2. **Multinomial Naive Bayes**

   * Works with **discrete counts** (e.g., word counts in documents).
   * Likelihood based on term frequency.
   * Commonly used in **text classification** and NLP.

3. **Bernoulli Naive Bayes**

   * Features are **binary** (0/1 → present or absent).
   * Suitable for text classification tasks where presence/absence matters more than count.

4. **Complement Naive Bayes**

   * A variant designed for **imbalanced datasets**.
   * Uses statistics from the complement of each class for better stability.

5. **Categorical Naive Bayes**

   * Works with **categorical features** directly without assuming numeric distribution.

## 📌 Key Takeaways

* Naive Bayes is simple yet powerful for classification tasks.
* Works best when features are **independent** and **non-correlated**.
* Choice of Naive Bayes type depends on the **nature of features** (continuous, discrete, binary, categorical).


# 🌸 Naive Bayes Classifier – Example

## 📌 Overview

This example demonstrates the use of **Gaussian Naive Bayes** to classify the **Iris flower dataset** into its three species based on sepal and petal measurements. Gaussian Naive Bayes is chosen because the features are continuous and approximately follow a normal distribution.

🔗 **View Notebook:** [Naive Bayes Iris Example](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Naive_Bayes_Classifier/Naive_Bayes_Example.ipynb)

---

## ⚙️ Workflow

1. **Dataset Loading:** Used the classic Iris dataset containing 150 samples with 4 features (sepal length, sepal width, petal length, petal width) and 3 target classes.
2. **Data Splitting:** Divided into **70% training** and **30% testing** data for evaluation.
3. **Model Training:** Applied **Gaussian Naive Bayes** to learn the conditional probability distributions.
4. **Prediction:** Classified unseen test data into one of the three Iris species.
5. **Evaluation:** Assessed model performance using a confusion matrix, accuracy score, and classification report.

---

## 🎯 Key Takeaways

* Gaussian Naive Bayes is highly effective when features follow a **normal distribution**.
* For well-separated classes like Iris species, it can achieve **perfect accuracy**.
* Works well with small datasets and minimal tuning.

---
