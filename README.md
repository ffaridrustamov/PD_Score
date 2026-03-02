What Was Done
1. Preprocessing
Missing values filled (mode for categorical, mean for numerical). Outliers identified in Age and InterestRate columns.
2. WoE Transformation
All features were binned into quartiles and encoded using Weight of Evidence, creating _woe columns for each variable.
3. Feature Selection
14 features with target correlation > 0.1 were selected. Intercorrelation between all pairs was confirmed below 0.7 (no multicollinearity).
4. Normality Test
Kolmogorov-Smirnov test confirmed all variables are non-normally distributed (p < 0.05).
5. Model Training
Two logistic regression models were built on a 70/30 train-test split:

Full model — 14 features → Test Gini: 59.58%
Reduced model — 4 features → Test Gini: 56.91% (selected)

The reduced model was chosen for its simplicity and similar performance. Selected features: OutstandingDebt_woe, InterestRate_woe, NumCreditInquiries_woe, Delayfromduedate_woe.
6. Deployment
The reduced model was applied to two production datasets (800 and 1,000 customers) to generate PD scores ranging from 0.088 to 0.710.
