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
```
## Deliverables
- [Deliverable 1: Data Collection, Cleaning, and Exploration](./MSCS-634-Deliverable1)
- [Deliverable 2: Regression Modeling and Performance Evaluation](./MSCS-634-Deliverable2)
- [Deliverable 3: Classification, Clustering, and Pattern Mining](./MSCS-634-Deliverable3)


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
