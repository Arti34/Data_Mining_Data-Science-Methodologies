# CRISP-DM Project Report: Predicting Telecom Customer Churn

**Student name:** Arti Ramesh Nalawade  
**Student ID:** 02075713  
**Project type:** Individual educational data science case study  
**Methodology:** CRISP-DM (six phases)  
**Data source:** Kaggle - `blastchar/telco-customer-churn`  
**Evidence:** Executed `crisp_dm_project_final.ipynb` (Google Colab)

## Executive summary (short overview)
Can a telecom company's retention team identify customers who might cancel their service? I followed the six CRISP-DM phases to build and evaluate a model that predicts which customers may stop using the service. The Kaggle dataset contains **7,043 rows and 21 columns**. Logistic regression was chosen based on validation-set F1 among three candidates. On a held-out set of **1,409 customers**, the selected model achieved **81% accuracy**, **0.60 F1 for churn**, **0.56 churn recall**, **0.66 churn precision**, and **0.842 ROC AUC**. These scores describe predictive performance on historical data, not proven improvements in retention or revenue.

## 1. Business understanding
**Business question:** Which customers may leave? A retention team could use a risk estimate to decide which customers should receive further review or support. The target `Churn` is whether the customer left (`Yes`) or stayed (`No`). A useful model needs to balance reaching at-risk customers (recall) against spending time on people who will stay (precision). Before real-world deployment, the business must define intervention costs, customer consent/privacy rules, acceptable error rates, and how success will be measured.

**Project success criteria:** produce a reproducible notebook; compare a simple baseline that always predicts the most common outcome and predictive models; select a model using validation data rather than final test data; report precision, recall, F1, ROC AUC (how well the model separates the two groups) and a confusion matrix (a table of right and wrong predictions); show saved-model inference.

## 2. Data understanding
The executed notebook downloaded Kaggle's public Telco Customer Churn dataset using `kagglehub`, reporting **7,043 records and 21 source columns**. It displays initial rows, data types, missing-value counts, duplicate-row counts, churn distribution, and a target-count plot. The notebook output reports **zero exact duplicate rows**. Categorical customer/service fields and numeric account fields are used to predict churn. `customerID` is treated as an identifier rather than a feature.

**Caution:** The dataset is historical observational data; a relationship does not prove that changing a feature would prevent churn.

## 3. Data preparation
`TotalCharges` is converted to numeric with invalid values becoming missing. The `customerID` field is removed, and churn is encoded as a binary outcome. The dataset is split using a **80/20 training/test split** that keeps roughly the same churn percentage in both groups, producing **5,634 training rows and 1,409 test rows**. The original modeling features number 19 (4 numeric and 15 categorical). Numeric columns are imputed with training-set medians and standardized. Categorical columns are imputed with training-set most-common values and one-hot encoded. All learned transformations are inside a scikit-learn pipeline, fitted only to the relevant training portion, reducing data leakage risk.

## 4. Modeling
Inside the training portion, a further stratified 25% validation split is used to compare three candidates using churn-class F1. Models use a consistent random seed (42).

| Candidate | Validation precision | Validation recall | Validation F1 | Validation AUC |
|---|---:|---:|---:|---:|
| Logistic regression | 0.660 | 0.535 | **0.591** | 0.836 |
| Random forest | 0.649 | 0.471 | 0.546 | 0.833 |
| Majority-class dummy baseline | 0.000 | 0.000 | 0.000 | 0.500 |

**Decision:** Logistic regression had the highest validation F1. The selected pipeline was then refitted using the full 5,634-row training portion. Final test labels were not used to choose the model.

## 5. Evaluation

| Final held-out test metric | Result |
|---|---:|
| Test samples | 1,409 |
| Accuracy | 0.81 |
| Churn precision | 0.66 |
| Churn recall | 0.56 |
| Churn F1 | 0.60 |
| ROC AUC | 0.842 |
| Actual churn examples in test data | 374 |
| Actual stay examples in test data | 1,035 |

**Interpretation:** About 81% of all test predictions were correct, but approximately 44% of actual churn customers were missed at the default threshold. This matters because finding likely churners is the business objective. A threshold study, calibration, outreach costs, and prospective testing would be needed before selecting a real campaign rule. This demonstration does not establish a causal effect or financial benefit.

## 6. Deployment demonstration and monitoring
The final pipeline was saved to `artifacts/churn_model.joblib`, reloaded, and used to predict one held-out input. The example received predicted churn probability **0.045 (4.5%)**, while its held-out label was **0 (stay)**. The notebook checks that the reloaded model's prediction equals the original model's prediction. A comparison table is saved to `artifacts/validation_model_comparison.csv`.

**Operational plan (proposal only):** monitor input missingness and feature drift; reassess prediction quality as labels arrive; review unequal errors across customer groups; evaluate business costs; retrain only with validation and oversight. No hosted application or operational monitoring service was built.

## AI critique and meaningful revision
An initial review found: (1) candidate comparisons were performed on the final test data; (2) business value was described without a measured cost/benefit framework; (3) critique claims lacked a clearly grounded external critique record. Changes: a validation subset was added for selection, the selected model was retrained on the original training portion, untouched-test evaluation was preserved, business assumptions were labeled as illustrative, and a critique section was added to the notebook. This constitutes **one documented critique cycle**, not multiple fabricated reviews.

## Limitations and next steps
- A fixed 0.5 classification threshold was used; no cost-sensitive threshold optimization was performed.
- Only one dataset and one held-out test split were used; performance may change on other customer populations.
- Fairness, calibration, business ROI and causal impact have not been quantitatively established.
- A historical test sample shows inference, but not a live operational system.

## Reproducibility and submission
Upload `crisp_dm_project_final.ipynb` into Google Colab, select **Runtime → Run all**, and ensure `DATA SOURCE: Kaggle: blastchar/telco-customer-churn` appears. Download the executed notebook and generated files from its Colab session. The notebook uses `kagglehub`, `pandas`, `numpy`, `matplotlib`, `scikit-learn` and `joblib`. Consult its output cells for the authoritative run-specific results.

**Dataset citation:** Kaggle: https://www.kaggle.com/datasets/blastchar/telco-customer-churn

## Key terms in simple words
- **Churn:** A customer stops using the service.
- **Training data:** Examples the model learns from.
- **Validation data:** Separate examples used to choose a model.
- **Test data:** Examples saved for the final, fair check.
- **Precision:** When the model predicts a customer will leave, how often is it right?
- **Recall:** Of all customers who actually leave, how many does the model find?
- **F1-score:** A combined score that balances precision and recall.
- **ROC AUC:** A score showing how well the model ranks likely leavers above likely stayers.
- **Inference:** Using a trained model to make a prediction for a customer.
