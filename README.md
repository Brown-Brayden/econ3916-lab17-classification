# econ3916-lab17-classification
# Classification: When 90% Accurate Is Worthless

## Objective
I fitted a loan-default classifier on simulated data with few defaults and chose a decision threshold from the cost of each kind of error, rather than from accuracy.

## Methodology
- Worked with 6,000 simulated loan applications, keeping 30% as test rows with the default rate the same in both sets.
- Fitted a logistic regression and compared its accuracy with a rule that approves everyone.
- Read the coefficients as log-odds and as odds ratios, and converted one odds ratio into changes in probability at three starting points.
- Traced precision and recall across six thresholds.
- Priced the two errors and chose the threshold with the lowest expected cost on the training rows, then priced it once on the test rows.
- Wrote a function, precision_recall_at(), that gives a classifier's precision and recall at any threshold.
- Checked whether the predicted probabilities were calibrated with a reliability diagram.

## Key Findings
- The default rate was 9.6%, so a rule that approves everyone was 90.4% accurate.
- At the usual 0.5 threshold, the model's accuracy was also 90.4%, with 0 predicted defaults: accuracy could not tell it apart from doing nothing.
- One more prior default multiplied the odds of default by 1.63, which meant a much larger change in probability for a risky applicant than for a safe one.
- The cost-minimising threshold was 0.121, close to the closed-form 0.118 and far below 0.5.
- At that threshold, the expected cost was 944 per applicant, against 1,147 at 0.5.
- At the closed-form threshold, precision was 0.181 and recall was 0.477.
- Calibration: the mean predicted probability was 0.096, equal to the observed default rate, and all ten bins sat close to the 45-degree line.
