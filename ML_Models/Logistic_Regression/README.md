# Logistic Regression: A Comprehensive Guide 📝

## About Logistic Regression 🤖🔢📊

Logistic Regression is a statistical and machine learning algorithm used for binary classification tasks. Unlike linear regression that predicts continuous outputs, logistic regression is used when the target variable is categorical, typically binary (0 or 1, True or False, Yes or No). It models the probability that a given input belongs to a particular category. 📈📌✅

The core idea is to fit a function to predict the probability of a class label based on one or more independent variables. This probability is then mapped using a threshold (commonly 0.5) to classify the instance into one of the categories. 🤝🧪⚖️

## Mathematical Analogy 🧮📐🔍

### Sigmoid Function:

The logistic regression model uses the sigmoid function to map the predicted values to a probability range between 0 and 1.

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

Where $z = w_0 + w_1x_1 + w_2x_2 + ... + w_nx_n$ is the linear combination of input features and weights.

This function ensures that outputs are within the range \[0,1], making them interpretable as probabilities. 🎯🔁📏

### Cost Function (Log Loss):

Logistic regression is trained using a loss function called Log Loss or Binary Cross Entropy:

$$
J(\theta) = - \frac{1}{m} \sum_{i=1}^{m} [y^{(i)} \log(h_\theta(x^{(i)})) + (1 - y^{(i)}) \log(1 - h_\theta(x^{(i)}))]
$$

Where:

* $h_\theta(x)$ is the predicted probability
* $y$ is the actual label
* $m$ is the number of training samples

This loss penalizes predictions that are far from the true labels. 📉🔍📘

### Optimization:

The model parameters (weights) are learned using optimization techniques like Gradient Descent, which iteratively updates weights to minimize the loss function. 🚀📉🔧

## Advantages 🌟📚🚀

* Easy to implement and understand
* Works well for linearly separable classes
* Outputs probabilities for class membership
* Less prone to overfitting in low-dimensional datasets
* Efficient for training and prediction on large datasets

## Limitations ⚠️📉⛔

* Assumes linear relationship between input variables and log-odds
* Not suitable for complex, non-linear problems
* Performance can degrade in presence of multicollinearity
* Sensitive to outliers
* Limited to binary or multiclass classification (not suitable for regression)

## Applications 🛠️🌐📦

* **Medical Diagnosis**: Predicting disease presence (e.g., diabetes, cancer)
* **Finance**: Credit scoring and fraud detection
* **Marketing**: Customer churn prediction
* **Social Science**: Predicting voting behavior
* **Industrial Use**: Predictive maintenance and fault classification

---

### 📌 Example: Logistic Regression in Action ✨✨✨

This example demonstrates how to use the `LogisticRegressionCustom` class on a synthetic dataset for binary classification:

* A dataset is generated using `make_classification` with 10 features and two classes.
* The data is split into training and testing sets.
* The logistic regression model is trained and used to predict outcomes.
* Model performance is evaluated using accuracy, classification report, and confusion matrix. ✅

To enhance performance:

* **GridSearchCV** and **RandomizedSearchCV** are used for hyperparameter tuning across solvers, penalties, regularization strengths, and class weights.
* The best parameters are automatically selected for optimal results. 🧠⚙️

Additional use cases covered:

* Multiclass classification using one-vs-rest strategy.
* Handling imbalanced datasets using weighted classes.
* Evaluating models with **ROC curves** and **AUC scores** for better insight. 📈📊

Check out the full notebook [here](https://github.com/ashay-thamankar/ml_models/blob/main/ML_Models/Logistic_Regression/Logistic_Regression_Example.ipynb) for complete implementation and visualization. 🔍📒

---
