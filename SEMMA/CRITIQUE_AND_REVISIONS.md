# SEMMA Critique and Revision Record

## Review focus

I reviewed the previous SEMMA notebook for consistency between the question and the code, fair model selection, repeatable results and clear communication.

## Issue 1 - Research question

Before: The wording suggested earlier grades were used, but `G1` and `G2` were excluded.

After: The question explicitly focuses on study habits, attendance and background information without earlier grades.

Verification: The input matrix drops `G3`, `G1` and `G2`.

## Issue 2 - Model selection

Before: The model comparison used the final test set, and Ridge was saved for the demo.

After: The notebook uses 237 training records and 79 validation records to choose the best model by MAE. It refits Random Forest on the combined 316 records and tests it once on the 79 held-out records.

Verification: Random Forest has the lowest validation MAE (3.182); final test MAE is 2.374.

## Issue 3 - Deployment demo and communication

After: The selected model is saved and reloaded, with an example prediction and limitation statement. The outputs are saved into `artifacts/`.

Verification: The notebook reports example prediction 8.69 and actual grade 5.0, and completes the save/load check.

## Transparency about AI critique

This record summarizes actual revisions from the ChatGPT-assisted assignment workflow. It does not represent a separately executed Claude or GPT-5 persona review. If the instructor wants those exact tools, run a real critique and add its dated prompt, findings and fixes here.
