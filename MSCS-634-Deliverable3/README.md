# MSCS 634 – Project Deliverable 3  

## Group Members:  
- Suresh Ghimire
- Sagar Bhetwal
- Nirajan Acharya
- Umesh Dhakal
- Enjal Chauhan

## Classification, Clustering, and Pattern Mining (Bank Marketing Dataset)

This deliverable applies multiple data mining techniques to the **Bank Marketing** dataset to generate actionable insights for marketing decision-making.  
The work covers:

- **Classification:** Predict whether a customer subscribes to a term deposit (`y`)
- **Clustering:** Segment customers into meaningful groups (unsupervised)
- **Association Rule Mining:** Discover common patterns linked to successful subscriptions

---

## Dataset

- **Raw data:** `data/raw/bank-full.csv`  
- **Processed (cleaned) data used for modeling:** `data/processed/bank-cleaned.csv`

> Note: The analysis is performed using the cleaned dataset to reduce noise and improve model stability.

---

## Folder Structure

```
MSCS-634-Deliverable3/
├── data/
│   ├── raw/
│   │   └── bank-full.csv
│   └── processed/
│       └── bank-cleaned.csv
├── notebooks/
│   └── MSCS_634_Project_Deliverable_3.ipynb
├── outputs/
│   └── figures/
│       ├── *.png
│      
├── tables/
│   ├── *.csv
├── requirements.txt
├── .gitignore
└── README.md
```

---

## How to Run

### Option A: Using `pip`
```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate

pip install -r requirements.txt
jupyter lab
```

### Option B: Using `uv` (if you are using uv in your environment)
```bash
uv venv
uv pip install -r requirements.txt
uv run jupyter lab
```

Open the notebook:

- `notebooks/MSCS_634_Project_Deliverable_3.ipynb`

---

## Methods Implemented

### 1) Classification (Supervised Learning)
Goal: Predict **term deposit subscription** (`y`).

**Models built and compared:**
- Logistic Regression
- Random Forest
- Linear SVM (baseline)
- Linear SVM (**tuned** using GridSearchCV)

**Evaluation approach:**
Because the dataset is imbalanced (many more “no” than “yes”), evaluation focuses on:
- **F1-score** and **ROC–AUC** (more informative than accuracy alone)
- Confusion matrices and ROC curves are generated and saved to `outputs/figures/`

### 2) Clustering (Unsupervised Learning)
Goal: Identify customer segments without using the target label.

**Approach:**
- K-Means clustering
- Elbow (inertia) and silhouette analysis to select `k`
- Best balance of interpretability + separation was achieved with **k = 4**
- Cluster plots are saved to `outputs/figures/`
- Cluster profiles and summaries are exported to `tables/`

### 3) Association Rule Mining (Apriori)
Goal: Identify combinations of attributes frequently linked to **successful subscriptions**.

**Approach:**
- Applied Apriori on records with `y = 1`
- Rules filtered using **support**, **confidence**, and **lift**
- Frequent itemsets and filtered rules are exported to `tables/`

---

## Key Results (from the notebook)

### Classification Performance Summary

| Model | Accuracy | Precision | Recall | F1-score | ROC–AUC |
|--------|-----------|-----------|--------|-----------|----------|
| Logistic Regression | 0.88 | 0.61 | 0.54 | 0.57 | 0.83 |
| Random Forest | 0.89 | 0.64 | 0.55 | 0.59 | 0.85 |
| Linear SVM (Baseline) | 0.87 | 0.60 | 0.55 | 0.57 | 0.84 |
| **Linear SVM (Tuned)** | **0.88** | **0.66** | **0.61** | **0.63** | **0.87** |

**Main takeaway:**  
Accuracy looks high for all models, but **F1-score and ROC–AUC** show the tuned SVM performed best overall, improving detection of likely subscribers.

---

### Clustering Summary (k = 4)

| Cluster | Avg Call Duration (sec) | Avg Balance | Previous Success Rate | Subscription Rate |
|-----------|--------------------------|-------------|-----------------------|-------------------|
| Cluster 0 | 95 | Low | Low | 4% |
| Cluster 1 | 140 | Medium | Moderate | 9% |
| Cluster 2 | 260 | High | High | 26% |
| Cluster 3 | 110 | Medium | Low | 6% |

**Main takeaway:**  
Cluster 2 had the highest engagement and subscription rate, suggesting outreach should prioritize customers with strong engagement signals and prior success history.

---

### Association Rule Mining (Examples)

| Antecedent | Consequent | Support | Confidence | Lift |
|--------------|-------------|----------|-------------|------|
| Previous Success + Long Duration | Subscription | 0.08 | 0.74 | 1.68 |
| Professional Job + High Balance | Subscription | 0.06 | 0.71 | 1.55 |
| Contacted in Previous Campaign + Success | Subscription | 0.05 | 0.76 | 1.72 |

**Main takeaway:**  
Rules repeatedly highlight **previous success** and **high engagement (duration)** as strong indicators of subscription.

---

## Outputs Produced

### Figures (`outputs/figures/`)
- Confusion matrices for each classifier  
- ROC curves (and other evaluation plots if enabled)
- K-Means elbow (inertia) plot and clustering visualization
- Model performance comparison chart

### Tables (`tables/`)
- Classification metrics summary table(s)
- Cluster sizes and numeric summaries
- “Top 5” cluster breakdowns (education, job, month, etc.)
- Frequent itemsets and filtered association rules

---

## Challenges / Decisions

- **Class imbalance:** Accuracy was not reliable alone, so **F1-score** and **ROC–AUC** were emphasized.
- **Preprocessing:** Consistent handling of numeric + categorical fields (imputation + scaling + one-hot encoding) improved stability.
- **Model tuning:** GridSearchCV was used to tune SVM parameters and improve minority-class detection.
- **Association rules:** Only the positive outcome group (`y = 1`) was mined to focus on patterns linked to successful subscriptions.

