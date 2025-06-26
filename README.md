### NTC Credit Risk Modeling

This project focuses on building a machine learning model to predict whether a **New-To-Credit (NTC)** customer will default or not. It is tailored for **startups or smaller lenders** that want to grow responsibly by minimizing risk.

---

### What

We use credit bureau and alternative data to:
- Predict if a borrower will **ever charge off** (binary classification)
- Estimate **expected loss amount** (regression)
- Calculate **PD%** (Probability of Default) and **NCL%** (Net Credit Loss)

---

## Why

Traditional lenders can afford to take bigger risks. Startups can’t. They need tools that:
- Prioritize **precision** to avoid approving risky accounts
- Segment borrowers by risk level before sending out pre-qualified offers
- Prevent costly defaults while still expanding their customer base

---

##  How

### 1. Data Collection & Understanding
- 28+ attributes per customer
- Targets: `Ever_ChargeOff`, `ChargeOff_Balance`

### 2. Data Cleaning & Feature Engineering
- Impute missing FICO with 999, flag with `No_Hit`
- Create `DTI = Total_Debt / Income`
- Remove outliers using IQR or 99th percentile
- Create feature bands: FICO, Income, Assets, etc.

### 3. Exploratory Data Analysis
- Distributions, class imbalance, and feature relationships
- Correlation heatmaps, leakage checks

### 4. Model Training & Thresholding
- Model: **Random Forest** with class_weight='balanced'
- Custom threshold = **0.5** for high precision
- Baseline comparison: Random Forest vs XGBoost

### 5. Validation & Cutoffs
- Evaluate PD% and NCL% by segments (e.g., FICO × Asset)
- Accept only segments where:
  - **PD% < 25%**
  - **NCL% < 10%**

### 6. Final Testing & Simulation
- Evaluate metrics: AUC, precision, RMSE
- Simulate default rates, approval rates, and loss
- Visualize outputs using Tableau

### Model Comparison & Evaluation

| Metric                | Random Forest | XGBoost  |
|-----------------------|---------------|----------|
| **Precision (Val.)**  | **0.667**     | 0.312    |
| **AUC (Val.)**        | **0.915**     | 0.944    |
| **Confusion Matrix**  | [[221, 11], [14, 5]] | [[225, 7], [13, 7]] |
### 7. Business Strategy & Deployment
- Use cross-tab logic for segment approval
- Implement rule-based offer strategy (green/red segmentation)
- Review thresholds quarterly




## Business Insight

> With a focus on the NTC population (e.g., young adults), this model helps lenders expand their market while managing risk conservatively. A higher precision threshold ensures fewer false positives, retaining more creditworthy new applicants.
