# Data Science Methodologies - CRISP-DM, KDD and SEMMA

**Student Name:** Arti Ramesh Nalawade  
**Student ID:** 02075713  

## Project Overview

This repository contains three data science projects that I completed to understand and apply three different data science methodologies: CRISP-DM, KDD, and SEMMA.

The main objective of this assignment is to learn how to approach a data science problem step by step, rather than directly building a machine learning model.

For each methodology, I selected a different dataset from Kaggle and completed the required stages using Python and Google Colab.

I also used AI-assisted reviews to identify areas for improvement, made necessary changes, and verified the results by executing the notebooks.

## 1. CRISP-DM - Customer Churn Prediction

**Project Title:** Predicting Customer Churn Using Machine Learning: A CRISP-DM Approach

**Dataset:** Telco Customer Churn (Kaggle)

**Objective:** Predict which telecom customers are likely to stop using the company's services.

This project follows all six stages of CRISP-DM:

1. Business Understanding
2. Data Understanding
3. Data Preparation
4. Modeling
5. Evaluation
6. Deployment

I explored customer information, prepared the data, trained machine learning models, and evaluated their performance.

The selected Logistic Regression model achieved approximately 81% accuracy. I also saved and reloaded the model to demonstrate how it can make predictions on new customer data.

**Medium Article:** [Can We Predict Which Customers Will Leave? My CRISP-DM Data Science Project](https://medium.com/@nalawade.arti/can-we-predict-which-customers-will-leave-my-crisp-dm-data-science-project-900be3022072?sharedUserId=nalawade.arti)

## 2. KDD - Market Basket Analysis

**Project Title:** Discovering Shopping Patterns Using Apriori: A KDD Approach

**Dataset:** Groceries Dataset (Kaggle)

**Objective:** Discover which grocery products customers frequently purchase together.

This project follows all five main stages of KDD:

1. Selection
2. Preprocessing
3. Transformation
4. Data Mining
5. Interpretation

I cleaned and transformed the grocery transaction data and applied the Apriori algorithm to discover frequent itemsets and association rules.

The final analysis identified 72 frequent itemsets and 5 association rules. I also verified the support and confidence calculations manually.

**Medium Article:** [What Do Customers Buy Together? Discovering Shopping Patterns Using KDD and Apriori](https://medium.com/@nalawade.arti/what-do-customers-buy-together-discovering-shopping-patterns-using-kdd-and-apriori-d4e0f0d953c2)

## 3. SEMMA - Student Performance Prediction

**Project Title:** Predicting Student Performance Using Machine Learning: A SEMMA Approach

**Dataset:** Student Alcohol Consumption (Kaggle)

**Objective:** Estimate students' final grades based on study habits, attendance, and background information without using earlier exam grades.

This project follows the five stages of SEMMA:

1. Sample
2. Explore
3. Modify
4. Model
5. Assess

I explored student information, prepared the data, and compared different machine learning models.

The selected Random Forest model achieved a Mean Absolute Error (MAE) of approximately 2.37 grade points and an R-squared value of 0.276.

These results show that student background information can help estimate grades, but the predictions are not always accurate.

**Medium Article:** [Can Study Habits Predict Student Grades? My Data Science Project Using SEMMA](https://medium.com/@nalawade.arti/can-study-habits-predict-student-grades-my-data-science-project-using-semma-4ad10f9f3c0b)

## 4. Video Walkthrough

I recorded a single video explaining all three projects.

The video includes:

- A brief introduction to each methodology
- The dataset used for each project
- A walkthrough of the Google Colab notebooks
- Important steps in data preparation and modeling
- Final results and observations
- AI-assisted improvements and validation

**YouTube Video:** [Data Science Methodologies - CRISP-DM, KDD and SEMMA](https://youtu.be/m8ocNCugkpQ)

## 5. Tools and Technologies

- Python
- Google Colab
- Pandas and NumPy
- Matplotlib
- Scikit-learn
- Apriori Algorithm
- Kaggle Datasets
- ChatGPT for code review and improvement
- GitHub for project documentation

## 6. Repository Structure

```text
Data-Science-Methodologies/
|
|-- CRISP-DM/
|   |-- Executed Colab notebook
|   |-- Project report
|   |-- AI critique and revisions
|   |-- README.md
|
|-- KDD/
|   |-- Executed Colab notebook
|   |-- Project report
|   |-- AI critique and revisions
|   |-- Generated artifacts
|   |-- README.md
|
|-- SEMMA/
|   |-- Executed Colab notebook
|   |-- Project report
|   |-- AI critique and revisions
|   |-- Generated artifacts
|   |-- README.md
|
|-- README.md
```

## 7. How to Run the Projects

1. Open any of the three project folders.
2. Download the corresponding `.ipynb` notebook.
3. Open [Google Colab](https://colab.research.google.com/).
4. Select **File > Upload notebook**.
5. Upload the downloaded notebook.
6. Select **Runtime > Run all**.
7. Review the outputs, charts, model results, and final artifacts.

The notebooks use publicly available Kaggle datasets. An internet connection is needed to download the datasets and install any missing Python packages.

## 8. What I Learned

By completing these three projects, I learned that different data science methodologies focus on different parts of the problem-solving process.

- **CRISP-DM** helped me understand how data science can be used to solve business problems.
- **KDD** helped me understand how useful patterns can be discovered from existing data.
- **SEMMA** helped me understand how to explore data, prepare features, compare models, and evaluate predictions.

I also learned that model performance alone is not enough. It is equally important to understand the dataset, check results, explain limitations, and document the work properly.

## 9. References

- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [Google Colab](https://colab.research.google.com/)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [IBM CRISP-DM Documentation](https://www.ibm.com/docs/en/spss-modeler/saas?topic=dm-crisp-help-overview)
