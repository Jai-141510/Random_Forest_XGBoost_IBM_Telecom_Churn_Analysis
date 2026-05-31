# Telecom-churn-prediction

Predicting which telecom customers are about to cancel, before they actually do.

---

## What this is

A classification project on the IBM Telco Customer Churn dataset. The dataset has 7,032 customers and 21 features covering their contract type, services, charges, and tenure. The target column is `Churn` that contains yes or no values

Two models were built and compared: Random Forest and XGBoost.

---

## The problem

Losing a customer costs 5–10x more than keeping one. If you can flag who's likely to churn a few weeks early, retention teams can act. This model does that flagging.

The dataset is imbalanced as only 27% of customers actually churned. That makes recall on the minority class the metric that matters most. Missing a churner is more expensive than a false alarm.

---

## What's in the notebook

1. **EDA** : churn patterns by contract type, charges, and tenure. Month-to-month customers churn fast and cheap; two-year customers who eventually leave paid a lot more before going.
2. **Preprocessing** : one-hot encoding for categoricals, label encoding for XGBoost's target requirement.
3. **Random Forest** : baseline with `class_weight='balanced'`. Good overall accuracy, weak churn recall.
4. **XGBoost** : `scale_pos_weight=2` to compensate for imbalance. Better churn recall, slightly lower overall accuracy.

---

## Results

| Model | Churn Recall | Churn F1 | Accuracy |
|---|---|---|---|
| Random Forest | 0.44 | 0.48 | 0.80 |
| **XGBoost** | **0.68** | **0.55** | 0.77 |

XGBoost wins. It catches 68% of real churners vs 44% with Random Forest. The accuracy drop is a deliberate tradeoff, it is worth it for the recall gain.

---
