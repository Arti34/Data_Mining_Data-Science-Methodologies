# SEMMA - Student Final Grade Prediction

Student: Arti Ramesh Nalawade  
Student ID: 02075713

This is my SEMMA project using the Kaggle `uciml/student-alcohol-consumption` dataset. My goal is to predict the final mathematics grade (`G3`) using student background and activity information without the earlier exam grades (`G1`, `G2`).

## Files

- `semma_project_revised_executed.ipynb` - Google Colab notebook, with saved execution outputs.
- `PROJECT_REPORT.md` - Full report using simple English.
- `MEDIUM_ARTICLE_DRAFT.md` - Draft to review and publish on Medium.
- `VIDEO_NOTES.md` - Short speaking notes for a combined three-project video.
- `CRITIQUE_AND_REVISIONS.md` - Evidence and summary of changes.

## Run the project

1. Open Google Colab and upload the notebook.
2. Choose Runtime > Run all.
3. Check that the source prints `Kaggle: uciml/student-alcohol-consumption`.
4. Review the validation model comparison, final test evaluation and example prediction.
5. Download `SEMMA_artifacts.zip` from the Files sidebar. Unzip it into an `artifacts/` subfolder when preparing GitHub.

## Results from my executed Colab notebook

- Data: 395 students, 33 original columns.
- Train / validation / test: 237 / 79 / 79.
- Model selected on validation: Random Forest.
- Final test: MAE 2.374, RMSE 3.184, R2 0.276.
- One demo: predicted grade 8.69; actual grade 5.0.

## Important limits

The model offers a rough estimate and should not be used as the only basis for real student decisions. The report and article are drafts for author review. No separately run external AI critique is claimed in this package.
