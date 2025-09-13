### 📌 Main Findings — Linear Regression Assumptions (README.md)
### 🔎 Project summary

We trained a linear regression model on a dataset with 3 features and 1 target (80:20 train-test split).
Below are the main findings (MF) regarding the classical assumptions of linear regression, how they were tested, and the conclusion for each.

### ✅ Assumption checks & results
### 1. Linearity

What we checked: scatter plots of each feature vs target.
What we observed: clear linear trends in the scatter plots.
Conclusion: Linearity assumption satisfied. The relationship between features and the target appears approximately linear.
<img width="998" height="258" alt="lr1" src="https://github.com/user-attachments/assets/7975cdb9-8d41-4aab-98a7-ceb89f46449f" />

### 2. Multicollinearity (No strong collinearity between predictors)

What we checked: correlation heatmap + Variance Inflation Factor (VIF) using statsmodels.stats.outliers_influence.variance_inflation_factor.
What we observed: VIF values are low (no values ≫ 5) and heatmap shows no strong pairwise correlations.
Conclusion: No problematic multicollinearity detected. Coefficient estimates should be stable.
<img width="515" height="418" alt="lr2" src="https://github.com/user-attachments/assets/ed782bb0-f5ed-4276-8aac-0ef1aef208dd" />


### 3. Normality of residuals

What we checked: residual histogram / KDE and Q–Q (probability) plot.
What we observed: residual distribution peaks near zero and Q–Q points lie approximately on the reference line.
Conclusion: Residuals are approximately normally distributed. This supports valid confidence intervals and hypothesis tests.
<img width="489" height="489" alt="lr3" src="https://github.com/user-attachments/assets/acf9fde0-0a33-4e05-bb3a-f607b9ed94a2" />
<img width="543" height="393" alt="lr4" src="https://github.com/user-attachments/assets/ace305fa-c378-4b9a-8d87-15fc6453e6e1" />


### 4. Homoscedasticity (constant variance of residuals)

What we checked: scatter plot of residuals vs. fitted values.
What we observed: residuals appear to form a roughly rectangular cloud (no funneling pattern).
Conclusion: Homoscedasticity holds approximately. No obvious heteroscedastic pattern detected.
<img width="557" height="413" alt="lr5" src="https://github.com/user-attachments/assets/66c70e23-7187-4794-8a3d-64f10cb1158a" />

### 5. No autocorrelation of residuals (independence)

What we checked: residuals plotted in sequence (and visually inspected for patterns).
What we observed: no systematic pattern or obvious correlation over order/time.
Conclusion: No strong autocorrelation detected. Residuals appear independent. (If this were time-series data, we’d add Durbin–Watson test.)
<img width="554" height="413" alt="lr6" src="https://github.com/user-attachments/assets/4ed288dc-6f18-4b2e-846a-5b795709cd95" />


### ⚠️ Overall assessment & next steps

All five classical assumptions (linearity, no strong multicollinearity, normality of errors, homoscedasticity, and residual independence) appear reasonably satisfied based on the diagnostic plots and VIF checks.

This indicates the linear regression model is appropriate for inference and prediction on this dataset — coefficient estimates and standard errors are likely reliable.

Recommended next steps (if you want to be thorough):

Run formal tests where applicable: Durbin–Watson (autocorrelation), Breusch–Pagan (heteroscedasticity).

If any assumption weakens on a larger dataset or new features, consider transformations, robust standard errors, or different models (e.g., GLM, tree-based models).
