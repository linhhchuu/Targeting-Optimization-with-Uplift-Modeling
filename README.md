# Starbucks Promotion Targeting Optimization: A/B Testing & Uplift Modeling

This project explores how Starbucks can optimize its promotional strategy using a combination of **A/B Testing** and **Uplift Modeling**. The goal is to move beyond blanket promotions and instead target customers who are most likely to respond, maximizing **Net Incremental Revenue (NIR)**.

---

## Problem Statement

Starbucks ran a randomized controlled experiment to test the effect of sending a $0.15 promotion to customers for a $10 product. While the promotion increased purchase likelihood, the overall campaign led to a **negative ROI** when sent to all users. This project investigates how to:

- Measure the **true causal effect** of the promotion.
- Identify **which customers** to target for **maximum revenue uplift**.

---

## Methods & Approach

### A/B Test Results
- **Response Rate Increase**: +0.95%
- **Statistical Significance**: p-value = 5.5e-36
- **Net Incremental Revenue**: **- $1,132** (due to cost of mass promotion)
<img width="1261" alt="image" src="https://github.com/user-attachments/assets/3828d8c6-4d05-4cf6-a59d-3d86be82106c" />

<img width="1263" alt="image" src="https://github.com/user-attachments/assets/1287b042-b5dd-4dd9-9296-5bab7c227174" />

### Uplift Modeling Pipeline
1. **Estimate Heterogeneous Treatment Effects (CATE)** using:
   - S-Learner
   - T-Learner
   - **X-Learner** (Best performer)
2. **Tune hyperparameters** with Optuna
3. **Score and rank customers** by individual uplift
4. **Target only the top uplift group** to improve ROI
<img width="1256" alt="image" src="https://github.com/user-attachments/assets/7bc8ca58-b914-4384-90bc-f78da3b42e92" />

---

## Results

| Model                 | Qini Score | IRR   | NIR     |
|-----------------------|------------|-------|---------|
| A/B Test (All users)  | N/A        | 0.95% | -$1,132 |
| S-Learner             | 0.2544     | 2.04% | $453    |
| T-Learner             | 0.2535     | 1.98% | $377    |
| **X-Learner (Tuned)** | **0.2794** | **2.06%** | **$541**  |

**Improvement over A/B mass targeting**: +$1,673
<img width="1264" alt="image" src="https://github.com/user-attachments/assets/455b3ee0-9174-4c9e-9186-4d4f4a42184f" />

---

## Tools & Tech

- **Python**: `pandas`, `scikit-learn`, `matplotlib`, `seaborn`
- **Causal Inference**: [`causalml`](https://github.com/uber/causalml)
- **Model Tuning**: `optuna`
- **Evaluation**: Qini Coefficient, Incremental Response Rate (IRR), Net Incremental Revenue (NIR)

---

## Key Learnings

- A/B testing can detect **if** something works, but **uplift modeling** reveals **for whom** it works best.
- A **data-driven targeting strategy** can significantly improve the cost-effectiveness of marketing campaigns.
- Business KPIs like **NIR** can (and should) drive model evaluation.

---
