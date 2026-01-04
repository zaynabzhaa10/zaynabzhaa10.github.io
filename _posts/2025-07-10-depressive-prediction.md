---
layout: post
title: "Depression Risk Prediction using Machine Learning & XAI"
date: 2025-07-10 09:00:00 +0800
categories: [Projects, Data Science]
tags: [Data Mining, Machine Learning, Depression]
image:
    path: "/assets/depressiveDisorder.png"
---

## Project Overview
Depression is one of the most common mental health disorders, yet many people do not receive early diagnosis or support.  
In this project, I developed a **machine learning model** to predict a person’s **risk of depression** using real-world health survey data.

The goal is to help identify individuals who may be at risk based on factors such as **stress, loneliness, physical health, and lifestyle**, so that **preventive actions** can be taken earlier.

---

## Data Source
The model is trained using data from the **Behavioral Risk Factor Surveillance System (BRFSS)**, a large-scale public health survey conducted in the United States.

The dataset contains information from thousands of adults and includes the following categories:

| Category | Examples |
|--------|----------|
| **Demographics** | Age, Gender, Race, Education, Income |
| **Health** | Diabetes, Asthma, Arthritis, BMI |
| **Lifestyle** | Physical activity, Smoking, Alcohol use |
| **Social Factors** | Stress, Loneliness, Emotional support, Life satisfaction |

**Target Variable:**  
Whether a person has ever been diagnosed with **depression**.

---

## How the Model Works
To predict depression risk, several machine learning models were implemented, chosen for their ability to handle complex, real-world data:

- Random Forest  
- Gradient Boosting  
- Histogram Gradient Boosting (HGB)

### Handling Data Imbalance
The dataset had an imbalance between depressed and non-depressed individuals.  
To address this, **SMOTE (Synthetic Minority Over-sampling Technique)** was applied.

### Model Optimization
- **Bayesian Optimization** was used to fine-tune hyperparameters  
- **SHAP (SHapley Additive exPlanations)** was used to interpret model predictions and understand feature contributions

---

## Results
The **Histogram Gradient Boosting (HGB)** model with hyperparameter tuning achieved the best performance.

### Model Performance
- **Accuracy:** 74%  
- **Precision:** 67%  
- **Recall:** 73%  
- **F1-Score:** 68%  
- **ROC AUC:** 81%

These results indicate that the model performs well in identifying individuals who may be at risk of depression.

---

## Key Factors Influencing Depression Risk
Based on SHAP analysis, the most influential features include:

- **Stress frequency** — how often an individual feels stressed  
- **Gender** — women showed higher risk  
- **Loneliness** — lack of emotional or social support  
- **Age group** — higher risk among young and middle-aged adults  
- **Race/Ethnicity** — certain groups are more affected  

These findings align with existing mental health research.

---

## Why This Matters
This project demonstrates how machine learning can support mental health initiatives by:

- Enabling early screening without invasive medical tests  
- Supporting healthcare professionals with data-driven insights  
- Guiding public health programs toward high-risk groups  
- Raising awareness of how daily life and social factors impact mental health  

---

## Limitations
- The data is **self-reported**, which may introduce bias  
- The model is trained on **U.S.-based data** only  
- Clinical and genetic information is not included  

---

## Future Work
Potential improvements and expansions include:

- Integrating real-time data (wearables, electronic medical records)  
- Exploring deep learning models for more complex patterns  
- Adapting the model for other countries, including **Indonesia**  

---

## Website Overview
An interactive web page is available to demonstrate how the model works and to visualize the results.

👉 **Project Repository:**  
[Depression Risk Prediction – GitHub Repository](https://github.com/khalikaa/depression-risk-prediction.git)

---

## Technologies Used
- Python  
- Scikit-learn  
- XGBoost / Gradient Boosting  
- SHAP  
- SMOTE  
- Bayesian Optimization  

---