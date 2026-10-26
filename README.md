# Week 6 Guided Practical Lab: Regression and Baseline Comparison
LYOMOKI JOHN 673396

## Lab Objective
Predict sales (KES) from advertising spend, store visits, discount percent, region, customer segment, and product category, and test whether a model adds real predictive value over simple baselines.

## Models Compared
- Mean Baseline
- Median Baseline
- Linear Regression
- Ridge Regression
- Decision Tree (shallow, and max_depth of 2, 4, 6, and None)

## Best Model
**Ridge Regression.** It had the lowest MAE and RMSE and the highest R² on the test set and in cross-validation. Linear Regression is practically tied, but Ridge's regularization makes it the safer choice.

## Selected Model Performance

| Metric | Test | Cross-validation |
|---|---|---|
| MAE | 13,714 KES | 15,971 KES |
| RMSE | 17,459 | 20,104 |
| R² | 0.870 | 0.848 |

Best baseline (Median) test MAE: 39,147 KES.

## Key Findings
1. **The model clearly beats the baselines and the trees.** Test MAE is about 65% lower than the best baseline, and the best Decision Tree (depth 6) had test MAE of 22,214. An unconstrained tree reached 0 training MAE but 26,798 on test, a clear case of overfitting.
2. **Errors are unbiased but uneven across groups.** Residuals center on zero with no clear pattern. The largest misses (up to about 48,000 KES) were mostly over-predictions in low-sales Nairobi Retail rows, and Retail had the highest segment MAE (15,561 vs 10,481 for SME).

## Limitations
1. **Small dataset and single split.** The test set has about 64 rows and segment groups have only 18 to 27, so results and subgroup comparisons are noisy.
2. **Missing external factors:** Competitor activity, holidays, and economic conditions are not captured.
3. **Single split and limited tuning:** Results come mainly from one train/test split, and depth was compared on test data, so some estimates may be optimistic.