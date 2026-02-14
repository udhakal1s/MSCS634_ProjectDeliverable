# MSCS_634_ProjectDeliverable_2

Deliverable 2: Regression Modeling and Performance Evaluation

## Group Members:  
- Suresh Ghimire
- Sagar Bhetwal
- Nirajan Acharya
- Umesh Dhakal
- Enjal Chauhan

## What’s included
- **Deliverable_2_Regression_Modeling.ipynb** – full code implementation with detailed comments, model evaluation, cross-validation, and visualizations
- **README.md** – summary of dataset, workflow, and results
- **requirements.txt** – dependencies
- **visualization** – visualization charts
- **data/bank-cleaned.csv** – the provided dataset

---

## Dataset
- **Source file:** `data/bank-cleaned.csv`
- **Size:** 45,211 rows × 22 columns  
- **Regression target (this run):** `age` (numeric)

---

## Modeling workflow (high level)
1. **Feature engineering**
   - `age_squared`
   - `pdays_was_missing`
   - `pdays_filled`
   - `campaign_per_previous`

2. **Preprocessing**
   - Numeric: median imputation + standard scaling  
   - Categorical: most-frequent imputation + one-hot encoding  

3. **Models**
   - Linear Regression
   - Ridge Regression
   - Lasso Regression

4. **Evaluation**
   - Train/test split (80/20)
   - K-fold cross-validation
   - Metrics: **R²**, **MSE**, **RMSE**

5. **Visualizations**
   - Model comparison plots (CV RMSE and CV R²)
   - Predicted vs Actual (best model)
   - Residual distribution

---

## Quick results snapshot (Target: `age`)
### Best Overall Model: Ridge Regression (`alpha=1.0`)
Based on cross-validation metrics and the performance report plots, **Ridge(alpha=1.0)** is the most consistent top performer.  
However, **Ridge and LinearRegression are essentially tied**—their scores are nearly identical—so the practical difference is minimal.

### Key metrics (summary)
#### Cross-validation (generalization)
- **Highest CV R² (mean)**
  - Ridge ≈ **0.981085**
  - LinearRegression ≈ **0.981085** *(tie)*
- **Lowest CV RMSE (mean)** *(lower is better)*
  - Ridge ≈ **1.460161** *(best by a tiny margin)*
  - LinearRegression ≈ **1.460164**
- **Stability**
  - Ridge and LinearRegression both show **very low std** across folds → consistent performance.

#### Test set (final evaluation)
- **Best Test R²**
  - Ridge and LinearRegression tie at ≈ **0.981067**
- **Lowest Test RMSE / MSE**
  - LinearRegression is *very slightly* lower than Ridge on Test RMSE/MSE, but the difference is tiny.

#### Lasso performance
- **Lasso** performs slightly worse than Ridge/LinearRegression:
  - Slightly lower R²
  - Slightly higher RMSE/MSE  
  This suggests Lasso’s shrinkage/feature selection did not provide an advantage for this dataset/target at this alpha.

---

## Insights from the plots
- **RMSE comparison:** RMSE values are extremely close across models - linear approaches perform similarly.
- **Explained variance (R²):** All models achieve **high R² (~0.98)** - strong predictive fit for `age`.
- **Predicted vs Actual (best model):** Points align closely with the trend line - predictions track actual values well.
- **Residual distribution:** Residuals are centered near **0** (low bias), with a **long tail** indicating occasional larger errors/outliers.

---

## Challenges encountered and how they were addressed
- **Mixed data types:** handled via `ColumnTransformer` pipelines.
- **Missing values (`pdays`):** imputation + explicit missing indicator feature.
- **Data leakage prevention:** preprocessing kept inside the pipeline used in CV.

---

## How to run
```bash
pip install -r requirements.txt
jupyter notebook Deliverable_2_Regression_Modeling.ipynb
