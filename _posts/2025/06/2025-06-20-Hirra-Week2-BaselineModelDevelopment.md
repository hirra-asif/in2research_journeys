---
title: "Week 2 – Baseline Model Development"
date: 2025-06-20
time: "17:00"
author: hirraa
categories: ["NLP", "machine learning", "social media"]
layout: post 
---

This week I focused on preparing the data splits, training baseline models, assessing their performance with multiple metrics and identifying challenges to address before moving on to deep learning models.

### Data Pipeline & Splits:

For each topic, the three datasets were individually shuffled and split 80/20 into training and testing sets using a stratified split (random_state=42). They were also combined, shuffled and split 80/20 to create training and testing sets containing examples from all sources.

---


### Baseline models trained:

I built three pipelines using feature embedding and extraction with TF-IDF vectorisation and Chi-Square feature selection. Four models were tested:

⭐  Multinomial Naïve Bayes – a probabilistic model based on Bayes’ theorem, suited for discrete features such as term frequencies, assuming feature independence.

⭐  XGBoost – a gradient boosting framework that builds an ensemble of decision trees in sequence, each one trained to minimise the errors made by the previous trees.

⭐  Logistic Regression – a linear model that estimates class probabilities using the logistic function.

⭐  Random Forest – an ensemble of decision trees trained on bootstrapped samples with random feature selection at each split.

Hyperparameters were tuned using 5-fold GridSearchCV, which tests multiple parameter combinations with cross-validation to balance bias and variance. For each model, the optimal hyperparameters were recorded and the corresponding best model was saved. 

---

### Performance: 

Model performance was evaluated using ROC AUC, precision, recall, balanced accuracy, F1-score, and specificity. For the multiclass COVID-19 task, all metrics were calculated using the macro averaging method.

---


**Challenges** 🤔❓
- Balancing two label schemes (binary ADR vs. multiclass sentiment) required custom evaluation scripts.  
- Hyperparameter searches via `GridSearchCV` introduce long training times and require more compute.
 - Class imbalance in ADR detection: most forum posts report reactions, so very few non-ADR examples, considering [`SMOTE`](https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.SMOTE.html)  to oversample the minority class could help address this.
---

➡️ **Up next**

`Deep Learning` 🧠 phase of the project implementing Transformer-based models (BERT and RoBERTa), training them on the cleaned dataset, and tuning hyperparameters for optimal performance.
