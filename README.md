# MSCS 634 – Project Deliverables (Deliverable 1–3)

## Group Members
- Suresh Ghimire
- Sagar Bhetwal
- Nirajan Acharya
- Umesh Dhakal
- Enjal Chauhan

This repository contains my project work for **MSCS 634 – Advanced Big Data and Data Mining** at the University of the Cumberlands.  
Each deliverable is organized in its own folder (Deliverable 1, Deliverable 2, Deliverable 3).

---

## Folder Structure

```
MSCS634_PROJECTDELIVERABLE/
├── MSCS-634-Deliverable1/
├── MSCS-634-Deliverable2/
└── MSCS-634-Deliverable3/
└── MSCS-634-Deliverable4/
```
## Deliverables
- [Deliverable 1: Data Collection, Cleaning, and Exploration](./MSCS-634-Deliverable1)
- [Deliverable 2: Regression Modeling and Performance Evaluation](./MSCS-634-Deliverable2)
- [Deliverable 3: Classification, Clustering, and Pattern Mining](./MSCS-634-Deliverable3)
- [Deliverable 4: Final Insights, Recommendations, and Presentation](./MSCS-634-Deliverable4)


### What each folder contains (high level)

- **`MSCS-634-Deliverable1/` — Data Collection, Cleaning, and Exploration**
  - Dataset selection + justification
  - Loading data with Pandas, inspecting structure
  - Cleaning (missing values, duplicates, inconsistent/noisy data)
  - EDA visualizations (distributions, outliers, feature relationships)
  - Written insights from EDA that guide later modeling

- **`MSCS-634-Deliverable2/` — Regression Modeling and Performance Evaluation**
  - Feature engineering steps used for regression
  - At least two regression models (example: Linear Regression + Ridge/Lasso)
  - Evaluation metrics (R², MSE, RMSE)
  - Cross-validation results
  - Summary of which model performed best and why

- **`MSCS-634-Deliverable3/` — Classification, Clustering, and Pattern Mining**
  - At least two classification models (example: Decision Tree, k-NN, Naive Bayes, SVM)
  - Hyperparameter tuning for one classification model
  - Evaluation: confusion matrix + ROC curve + Accuracy/F1
  - At least one clustering model (example: K-Means, Hierarchical, DBSCAN) + visual explanation
  - Association rule mining (example: Apriori or FP-Growth) + real-world interpretation

- **`MSCS-634-Deliverable4/` — **Final Insights, Recommendations, and Presentation**
  - Consolidated summary of **Deliverable 1–3** (what was done + why it matters)
  - Dataset recap: **what dataset**, **why chosen**, and **what problem it solves**
  - Key insights from:
    - preprocessing decisions (unknown handling, `pdays` meaning, encoding strategy)
    - EDA highlights (imbalanced target, outliers/skew, strongest relationships)
    - feature engineering (indicators, transformations, bins if used)
  - Results recap (short + clear):
    - Regression: best model + key metrics (**R², RMSE**) + 1-line interpretation
    - Classification: best model + tuning summary + metrics (**Accuracy/F1 + ROC**) + what it implies
    - Clustering: chosen `k` + silhouette/elbow reasoning + cluster meaning (2–3 lines)
    - Association rules: top rules + **real-world interpretation** (not just support/confidence)
  - Practical recommendations (actionable, business-style):
    - what to do next based on regression/classification insights
    - how to use clusters for segmentation
    - how to use rules for targeting or messaging themes
  - Ethical considerations:
    - privacy risks (sensitive attributes, customer targeting)
    - fairness/bias risk (groups impacted, imbalance)
    - mitigation steps (metrics beyond accuracy, transparent pipeline, careful feature use)
  - Visualizations included (placeholders with correct names):
    - `[IMAGE: target_distribution.png]`
    - `[IMAGE: correlation_heatmap.png]`
    - `[IMAGE: outlier_boxplots.png]`
    - `[IMAGE: model_performance_report.png]`
    - `[IMAGE: confusion_matrix_linear_svm_tuned.png]`
    - `[IMAGE: roc_curve_linear_svm_tuned.png]`
    - `[IMAGE: kmeans_elbow_inertia.png]`
    - `[IMAGE: kmeans_silhouette_scores.png]`
    - `[IMAGE: kmeans_clusters_truncatedsvd_scatter.png]`
    - `[IMAGE: top_rules_output.png]`
  - Submission items:
    - GitHub repo link: `[https://github.com/udhakal1s/MSCS634_ProjectDeliverable]`
    - 5–7 minute presentation video link: `[https://cumber-my.sharepoint.com/:v:/g/personal/sghimire38288_ucumberlands_edu/IQB1BVQMvYzYRpO1aTxZtL9_AWdTyp1k6KVN8aDbIXuOG1E?nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D&e=n0WSLo]`

---
## Recommended Contents Inside Each Deliverable Folder

Each deliverable folder typically includes:

- `*.ipynb` notebook(s) with code + outputs
- `README.md` (deliverable-specific summary + insights)
- `data/` (raw and/or cleaned datasets, if allowed to submit)
- `screenshots/` (screenshots of key steps and results, if required)

Example (adjust names to match your files):

```
MSCS-634-DeliverableX/
├── MSCS_632_DeliverableX.ipynb
├── README.md
├── data/
│   ├── raw.csv
│   └── cleaned.csv
└── screenshots/
    ├── step1.png
    ├── step2.png
    └── ...
```

---

## Notes for Submission

For each deliverable, the submission normally includes:
- **Jupyter Notebook (.ipynb)** with clear, well-commented code, tuning explanation, and visualizations.
- **data/** contains the dataset used in this deliverable:
  - `data/raw/` - original dataset (unchanged)
  - `data/processed/` - cleaned / transformed dataset used for modeling (ex: `bank-cleaned.csv`)
  - `data/README.md` - short description of each file and key columns

- **visualizations/** contains plots exported from the notebook:
  - EDA plots (distributions, missing values, outliers)
  - Model evaluation plots (confusion matrix, ROC curve, elbow plot, cluster visualization)
  - Files saved as `.png` (example: `visualizations/step2_outliers.png`)

- **README.md** summarizing key insights, practical relevance, and challenges + how they were handled.

---
