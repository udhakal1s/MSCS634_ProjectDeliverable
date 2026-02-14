# MSCS 634 – Project Deliverable
## Data Collection, Cleaning, and Exploration (EDA)

## Group Members:  
- Suresh Ghimire
- Sagar Bhetwal
- Nirajan Acharya
- Umesh Dhakal
- Enjal Chauhan

### Dataset Summary
- **File:** `data/bank-full.csv`
- **Rows / Columns:** 45,211 rows × 17 columns
- **Target:** `y` (term deposit subscription: yes/no)

This dataset is well-suited for the project because it exceeds the minimum dataset size requirement and includes a strong mix of numeric and categorical variables, enabling meaningful preprocessing, EDA, and later modeling work.

### Repository Contents
* **`data/`** – Contains the raw dataset (`bank-full.csv`).
* **`visualization/`** – Directory containing exported charts and EDA figures.
* **`Deliverable1.ipynb`** – Main Jupyter notebook containing data processing and analysis.
* **`requirements.txt`** – Python dependencies required to run the environment.
* **`README.md`** – Project documentation and summary.

### Data Cleaning Steps Performed
1. **Column name standardization:** lowercase + replace `.` with `_`
2. **Target encoding:** `y` converted from `{yes,no}` to binary `{1,0}`
3. **Handling sentinel values in `pdays`:**
   - `pdays = -1` indicates “not previously contacted”
   - converted to `NaN` and a new indicator feature **`prev_contacted`** was added
4. **Handling categorical `"unknown"` values:**
   - verified the dataset contains no explicit `NaN` values, but several columns use `"unknown"` to indicate missing/unspecified
   - created missingness indicator flags (e.g., `contact_unknown`, `poutcome_unknown`) to preserve the information
5. **Type optimization:** categorical string columns converted to `category` dtype for clarity and efficiency

**Notes on missing/unknown values (counts in the raw dataset):**
- `poutcome = "unknown"`: 36,959
- `contact = "unknown"`: 13,020
- `education = "unknown"`: 1,857
- `job = "unknown"`: 288

### Key Insights

Based on the EDA above, here are the main takeaways:

1. **Class imbalance:** the positive class (subscription) is much smaller than the negative class → use stratified splits, class weights, and metrics like F1/ROC-AUC later.
2. **Strong drivers of subscription:**
   - **`duration`** is typically much higher for successful subscriptions.  
      *However, duration is measured **after** the call ends, which can cause **data leakage** if the goal is “predict before calling”.*
   - **`poutcome`** and previous-contact information are highly informative (when available), but many values are unknown.
3. **Missingness-as-signal:** `"unknown"` values are common in some categorical columns (especially `poutcome` and `contact`). Missing indicators can help models learn patterns in “unknown-ness”.
4. **Skew and outliers:** variables like `balance`, `duration`, `campaign`, and `previous` are heavy-tailed.  
   → consider log/robust scaling or outlier capping for some models.
5. **Seasonality effects:** `month` shows major differences in subscription rates across months → consider encoding month with an ordered category or cyclical transform.


### Challenges Encountered & How They Were Addressed
- **No explicit missing values:** Instead, missingness is encoded as `"unknown"` in multiple fields.  
  → Addressed by adding **indicator flags** and keeping `"unknown"` as a valid category.
- **Sentinel values (`pdays = -1`):**  
  → Converted to `NaN` and added `prev_contacted` to avoid confusing “not contacted” with a numeric day count.
- **Highly skewed numeric variables:**  
  → Documented via histograms/boxplots; outlier handling is deferred to later deliverables (feature engineering/model choice).

### How to Run
```bash
pip install -r requirements.txt
jupyter notebook
```


### Setup & Run (uv)
``` bash
uv venv

# macOS/Linux
source .venv/bin/activate
# Windows (PowerShell)
# .\.venv\Scripts\Activate.ps1

uv pip install -r requirements.txt
jupyter notebook

```

Open **`Deliverable_1.ipynb`** to view the full analysis with plots.
