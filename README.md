# Enhancing Transparency in Rainfall Prediction with Explainable Artificial Intelligence

This project investigates how **Explainable Artificial Intelligence (XAI)** can improve the transparency, trustworthiness, and practical usefulness of a **rainfall prediction system**. The system is built on the **Rain in Australia** dataset and uses an **XGBoost classifier** for binary prediction of whether it will rain the next day.

To make the model more understandable, the project applies two post-hoc, model-agnostic explanation methods:

- **Kernel SHAP** for feature importance analysis
- **DiCE** for counterfactual explanations

The project is designed to show not only **how well** the model predicts rainfall, but also **why** it makes its predictions and **what changes** could alter the predicted outcome.

---

## Overview

In real-world forecasting tasks, predictive accuracy alone is often not enough. Users also need to understand the reasoning behind a model’s output. This is especially important in rainfall prediction, where forecasts can influence:

- agricultural planning
- water resource management
- infrastructure preparation
- disaster response

This project demonstrates how XAI techniques can support different stakeholders by making a black-box model more transparent and actionable.

---

## Problem Statement

Rainfall prediction models can achieve strong performance, but many machine learning methods are difficult to interpret directly. Without explanations:

- domain experts may struggle to validate the model
- decision-makers may not know how to use predictions effectively
- end users may distrust the system

This project addresses that challenge by combining **XGBoost** with **Kernel SHAP** and **DiCE**, providing both descriptive and actionable explanations.

---

## Stakeholders and Explainability Needs

This project considers several stakeholder groups:

- **Meteorologists and environmental analysts**  
  Need technically meaningful explanations to verify whether the model relies on scientifically reasonable features.

- **Government agencies**  
  Need trustworthy predictions for infrastructure planning and emergency response.

- **Farmers and agricultural planners**  
  Need understandable, actionable insights to support crop and irrigation decisions.

- **General public**  
  Need transparency and reliability to trust automated rainfall forecasting systems.

To address these different needs, the project adopts a stakeholder-oriented XAI strategy.

---

## XAI Strategy

Two complementary explanation methods are used:

### 1. Kernel SHAP
Kernel SHAP is used mainly for **feature importance analysis**.

It helps answer questions such as:
- Which meteorological variables are most important?
- How much does each feature contribute to a prediction?
- Are the learned patterns aligned with domain knowledge?

This is especially useful for technical stakeholders such as meteorologists and analysts.

### 2. DiCE Counterfactual Explanations
DiCE is used to generate **counterfactual explanations**.

It helps answer questions such as:
- What small changes in the input could reverse the prediction?
- Which conditions are most actionable for decision-making?

This is particularly valuable for non-technical users and planners, because it expresses explanations as “what-if” scenarios.

---

## Dataset

This project uses the **Rain in Australia** dataset, which contains daily meteorological observations collected from multiple weather stations across Australia.

### Target Variable
- **RainTomorrow**
  - `1` = rain tomorrow
  - `0` = no rain tomorrow

### Selected Features
After preprocessing, nine relevant meteorological features were selected to simplify the model while maintaining predictive power. These include variables related to:

- temperature
- humidity
- wind conditions
- atmospheric pressure
- recent rainfall indicators

### Preprocessing
- removed incomplete records
- selected relevant features
- encoded the target variable for binary classification

This preprocessing strategy improves consistency, although removing missing values may reduce dataset size and potentially introduce bias.

---

## Model

The predictive model used in this project is an **XGBoost classifier**.

### Why XGBoost?
XGBoost was chosen because:
- it performs well on structured tabular data
- it can model nonlinear relationships
- it captures complex feature interactions
- it is widely used in real-world predictive tasks

However, XGBoost is not inherently interpretable, which makes it a strong candidate for post-hoc explainability methods.

---

## Explainability Methods

## 1. Kernel SHAP

Kernel SHAP is a **post-hoc, model-agnostic** explanation method based on **Shapley values** from game theory.

### Classification
- **Scope:** Local and Global
- **Timing:** Post-hoc
- **Model Dependency:** Model-agnostic

### Purpose in This Project
Kernel SHAP is used to:
- explain global feature importance
- interpret individual predictions
- validate whether the model relies on meaningful meteorological variables

### Key Finding
The results show that **humidity-related variables** and **pressure indicators** are among the most influential features in rainfall prediction, which is consistent with domain knowledge.

---

## 2. DiCE Counterfactual Explanations

DiCE is a **post-hoc, model-agnostic** method for generating **diverse counterfactual explanations**.

### Classification
- **Scope:** Local
- **Timing:** Post-hoc
- **Model Dependency:** Model-agnostic

### Purpose in This Project
DiCE is used to:
- generate alternative scenarios
- show how small changes in input variables can change the prediction
- provide actionable explanations for users and decision-makers

### Key Finding
Counterfactual examples show that changes in variables such as **humidity** and **Cloud3pm** can reverse the predicted rainfall outcome.

---

## Model Performance

The XGBoost model was evaluated using standard binary classification metrics:

- Accuracy
- Precision
- Recall
- F1-score

The report indicates that the model achieved **reasonable predictive performance** on unseen test data, showing that it can learn meaningful patterns from the selected meteorological features.

At the same time, the project emphasizes that **performance metrics alone are not sufficient**, because they do not explain how predictions are produced.

---

## Key Insights

### Why Explainability Matters
In rainfall prediction, explainability improves:

- **transparency**
- **trust**
- **accountability**
- **decision support**

### Why Kernel SHAP and DiCE Work Well Together
These two methods offer complementary perspectives:

- **Kernel SHAP** explains **which features matter** and **how much**
- **DiCE** explains **what needs to change** to obtain a different outcome

Together, they support both:
- technical understanding
- practical decision-making

---

## Repository Structure

```text
.
├── README.md
├── notebooks / scripts
├── figures
└── related project files
```

You can update this section based on your actual repository structure.

---

## Project Workflow

```text
Rain in Australia Dataset
        ↓
Data preprocessing and feature selection
        ↓
XGBoost model training
        ↓
Performance evaluation
        ↓
Kernel SHAP global and local explanations
        ↓
DiCE counterfactual generation
        ↓
Interpretation for stakeholders
```

---

## Tech Stack

- **Python**
- **XGBoost**
- **Pandas**
- **NumPy**
- **Scikit-learn**
- **Kernel SHAP**
- **DiCE**
- **Matplotlib / visualization tools**
- **Jupyter Notebook**

---

## Key Features

- Rainfall prediction using a strong tabular ML model
- Explainability analysis with **Kernel SHAP**
- Counterfactual explanation generation with **DiCE**
- Stakeholder-oriented XAI strategy
- Combination of predictive performance and interpretability
- Real-world XAI case study for environmental forecasting

---

## Potential Impact

Applying XAI in this system provides several important benefits:

- improves user trust in rainfall forecasts
- helps identify unreasonable feature dependencies
- supports more informed decision-making
- increases transparency and accountability
- makes the prediction system more useful in real-world settings

---

## Limitations

- removing missing values may reduce data size and introduce bias
- XGBoost remains a black-box model internally
- post-hoc explanations are approximations of model behavior
- generating explanations may increase computational cost
- counterfactual explanations are useful, but they do not guarantee causality

---

## Future Improvements

- compare more interpretable and non-interpretable models
- add clearer visualizations of SHAP and counterfactual results
- improve preprocessing for missing values instead of simple row removal
- deploy the system as an interactive XAI demo
- evaluate explanation usefulness with real stakeholders

---

## Why This Project Matters

This project demonstrates practical experience in:

- **tabular machine learning**
- **XGBoost classification**
- **Explainable AI (XAI)**
- **feature attribution with SHAP**
- **counterfactual explanation generation**
- **stakeholder-aware AI system design**

It is a strong portfolio project for roles related to:

- AI / ML engineering
- explainable AI
- applied machine learning
- decision-support systems
- trustworthy AI

---

## Author Contribution

**Tian Zhennan**  
Contributed to the XAI-based rainfall prediction project, including dataset preprocessing, model building, explainability analysis, and report preparation.

---

## Conclusion

This project shows that explainability is essential for making rainfall prediction systems more transparent and trustworthy.

By combining **XGBoost** with **Kernel SHAP** and **DiCE**, the system can provide both:

- accurate predictive modeling
- understandable and actionable explanations

Overall, the project highlights how XAI can bridge the gap between model performance and real-world usability in environmental forecasting.

---

## References

- Rain in Australia dataset
- XGBoost
- Kernel SHAP
- DiCE
