# SEMMA Project Report: Predicting Student Final Grades

**Student:** Arti Ramesh Nalawade  
**Student ID:** 02075713  
**Methodology:** SEMMA (Sample, Explore, Modify, Model, Assess)

## 1. My project question

Can I estimate a student's final mathematics grade using study habits, attendance and other background information without using earlier exam grades?

My answer is that I can make a rough estimate, but I cannot predict every student's grade accurately. I used the SEMMA steps to find out what the available data can tell me.

## 2. Dataset and objective

I used the `student-mat.csv` dataset from Kaggle, `uciml/student-alcohol-consumption`. Each row represents one student. The dataset contains **395 students and 33 columns**. The final grade is called `G3`, and grades run from 0 to 20. I excluded `G1` and `G2`, the earlier grades, so the project tests the value of other information. This is an experiment, not a tool to decide what should happen to a real student.

## 3. Stage 1 - Sample

I loaded the file and checked that the three grade columns existed. I divided the data into **237 training records, 79 validation records and 79 final test records**. Training means the model learns patterns. Validation helps me pick the model. Testing checks the selected model on data I kept aside. I used the same random seed so someone else can repeat the process.

## 4. Stage 2 - Explore

I checked missing entries, duplicate rows and a chart of final grade distribution. The dataset had **0 missing values and 0 duplicate rows** in this run. There were 13 numeric inputs and 17 categorical inputs after excluding the grade columns. An example of a numeric input is age or absences. A categorical input might be school or a yes/no answer. Seeing a relationship in the data does not prove that one factor causes better grades.

## 5. Stage 3 - Modify

I prepared the data so the computer could use it. Missing numbers would be filled with a typical value, and missing categories with the most common value. I scaled numeric data and converted categories into indicator columns. These operations were placed in a pipeline that learns its transformation settings from training data, not from the final test data.

## 6. Stage 4 - Model

I compared three approaches: a mean baseline, Ridge Regression and Random Forest. The baseline predicts the average grade and helps show whether the other models offer an improvement. Ridge Regression looks for a relatively simple relationship. Random Forest combines many decision trees.

I used **validation MAE** to choose the model. Lower MAE means smaller average mistakes.

| Model | Validation MAE | Validation RMSE | Validation R2 |
|---|---:|---:|---:|
| Random Forest | 3.182 | 4.406 | 0.284 |
| Mean baseline | 3.917 | 5.236 | -0.011 |
| Ridge Regression | 4.152 | 5.218 | -0.004 |

**Random Forest was selected**, because it had the lowest validation MAE. I then trained it again using the training plus validation records, while leaving the final test set untouched.

## 7. Stage 5 - Assess

I evaluated the selected Random Forest on the 79 final test records.

| Final test measure | Result |
|---|---:|
| MAE | 2.374 |
| RMSE | 3.184 |
| R2 | 0.276 |

**What this means in normal language:** The predicted grade differs from the true grade by about **2.37 grade points on average**, on a 0 to 20 grading scale. An R2 of 0.276 means the model explains some variation but misses a lot. It should not be used on its own to make real decisions about students.

A scatterplot in my notebook compares predicted and actual grades. Points farther from the diagonal line represent bigger prediction errors.

## 8. Practical prediction demo

Although SEMMA itself ends at Assess, I also saved and reloaded the selected model to show that a prediction can be made. For one example student, the model predicted **8.69** while the actual grade was **5.0**. One example is not enough to evaluate a model, which is why I also reported MAE and R2 across the whole test set.

The notebook saves `student_grade_pipeline.joblib`, `validation_model_comparison.csv` and `final_test_metrics.csv` in the Colab `artifacts` folder. Those files should be downloaded from Colab and included in the GitHub repository.

## 9. Critique and revisions

During the review of my earlier SEMMA notebook, I identified and corrected these issues:

1. **The research question was inconsistent with the code.** Earlier grades were mentioned but not used. I changed the question to clearly say that G1 and G2 are excluded.
2. **The original model comparison relied on the final test set.** I introduced a separate validation set to select the model, then assessed the chosen model on an untouched final test set.
3. **The saved demonstration model was not the strongest according to the comparison.** The updated code now saves the model chosen from validation results.
4. **The limitations needed a clearer explanation.** I now describe the output as a rough estimate and note the risk of using it for individual students.

These notes document feedback and revisions from the assignment workflow. They are **not proof of a separately run GPT-5 or Claude review**. Any additional external AI critique must be genuinely performed and saved as evidence.

## 10. Limitations and future improvements

The dataset is small and comes from a particular school context, so it may not represent other students. The model can make large mistakes. I did not check subgroup fairness or test it on a different school. In future, I could compare simpler feature sets, examine important errors, and study whether the predictions are equally reliable for different groups. A real school should not rely on this model without proper evaluation, consent and safeguards.

## 11. Conclusion

I completed all five SEMMA stages on a Kaggle student dataset. Random Forest performed best on the validation set. Its final MAE of 2.374 shows that study habits, attendance and background data can support a rough grade estimate, but the estimate is not precise enough to treat as a student's real outcome.

**Source:** Kaggle `uciml/student-alcohol-consumption` (`student-mat.csv`). All numeric results above come from the executed Colab notebook.
