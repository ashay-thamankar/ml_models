# Apriori Algorithm – Market Basket Analysis 🛒✨

## About 📖

The **Apriori algorithm** is a classic machine learning technique used for **association rule mining**. It helps uncover hidden patterns, correlations, and relationships between items in large transactional datasets. The algorithm is widely applied in **market basket analysis**, where the goal is to discover which items are frequently bought together (e.g., "if a customer buys bread, they are likely to buy butter").

It works by finding **frequent itemsets** in a dataset and then generating **association rules** that describe how the presence of certain items influences the likelihood of others appearing.

---

## How It Works ⚙️

1. **Frequent Itemset Generation**

   * Identify all itemsets (groups of items) that appear frequently in the dataset, based on a minimum threshold called **support**.
   * The key principle: *Any subset of a frequent itemset must also be frequent* (Apriori property).

2. **Association Rule Generation**

   * From the frequent itemsets, generate rules of the form **X → Y**, where X and Y are disjoint itemsets.
   * These rules describe relationships like "If X occurs, then Y is likely to occur."

3. **Evaluation of Rules**
   Rules are evaluated using three main metrics:

   * **Support(X → Y)** = P(X ∪ Y)
   * **Confidence(X → Y)** = P(Y|X) = Support(X ∪ Y) / Support(X)
   * **Lift(X → Y)** = Confidence(X → Y) / Support(Y)

     * If **Lift > 1** → X and Y are positively correlated.
     * If **Lift = 1** → X and Y are independent.
     * If **Lift < 1** → X and Y are negatively correlated.

---

## Mathematical Intuition 🔢

* Let’s denote a transaction dataset as **T**, containing sets of items.
* For an itemset **I**,

Support:

```
Support(I) = (Number of transactions containing I) / (Total number of transactions)
```

Confidence:

```
Confidence(X → Y) = Support(X ∪ Y) / Support(X)
```

Lift:

```
Lift(X → Y) = Confidence(X → Y) / Support(Y)
```

Example equation format:

* Suppose β₀ represents the **support threshold**, then:

  * Keep only itemsets **I** where Support(I) ≥ β₀

This ensures we only focus on the most meaningful and frequent patterns.

---

## Advantages ✅

* **Easy to understand**: Intuitive, rule-based approach for pattern discovery.
* **Interpretable results**: Provides clear "if-then" association rules.
* **Proven & widely used**: Trusted in retail, healthcare, finance, and more.
* **Scalable**: Can work on large datasets (with optimizations).
* **No distribution assumptions**: Works directly on transactional data.

---

## Limitations ⚠️

* **Computationally expensive**: Generates a large number of candidate sets, especially with low thresholds.
* **Requires parameter tuning**: Choosing proper values of **support**, **confidence**, and **lift** is critical.
* **Not suitable for continuous data**: Works only with categorical or discretized data.
* **May produce trivial rules**: Some discovered rules may not be useful or actionable.

---

## Applications 🌍

* **Retail / E-commerce**: Market basket analysis (e.g., Amazon, Walmart recommending items).
* **Healthcare**: Finding co-occurrence of symptoms and treatments.
* **Telecommunications**: Detecting service bundling and customer usage patterns.
* **Finance**: Identifying co-purchase of financial products or fraud detection.
* **Web Usage Mining**: Understanding browsing patterns for better recommendations.

---

## Reference Link 🔗

For more details and implementation, check out:
[Apriori Algorithm on GitHub](https://github.com/ashay-thamankar/ml_models)

---