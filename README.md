# Hierarchical vs Flat Machine Learning for Intrusion Detection

## Overview
This research project compares **Flat** and **Hierarchical** machine learning approaches for Intrusion Detection Systems (IDS) using the **UNSW-NB15 dataset**.

We investigate whether decomposing attack detection into a two-stage pipeline improves:

- Rare attack detection
- Macro F1-score
- Overall system reliability

---

## Research Question

> Does a hierarchical classification framework outperform a flat multi-class classifier for intrusion detection?

---

## Architecture

### Flat Model

- Single multi-class classifier
- Direct prediction of attack category
- RandomForest + Optuna tuning
- SMOTE + Undersampling


---

### Hierarchical Model
##### Two-stage detection pipeline.
#### Stage 1 — Binary Detection

- Model: XGBoost
- Binary Classification: Attack vs Normal
- Class-weighted training
- Threshold-based prediction (default = 0.3)


---

#### Stage 2 — Attack Refinement

Triggered only if Stage 1 predicts **Attack**

- Trained only on attack samples
- RandomForest
- Hyperparameter tuning via Optuna
- Adaptive resampling (target_count)
- SMOTE balancing


## Technologies Used
- **Python**
- **Scikit-Learn**
- **xgboot**
- **imblearn**
- **Pandas & NumPy**
- **Optuna** (for advanced optimization)

## Results & Insights
### Performance Comparison

| Model        | Accuracy | Macro F1 | Weighted F1| Attack Recall |
|--------------|----------|----------|------------|---------------|
| Flat         | 0.7937   | 0.5644   | 0.8128     | 0.6768        |
| Hierarchical | 0.8402   | 0.5855   | 0.8519     | 0.6745        |


---
## Key Findings
- Binary Detection is Extremely Reliable, with very high ROC-AUC (~0.999), it provides a stable separation between Normal and Attack traffic.
- The hierarchical framework trained Stage 2 only on attack samples and applied adaptive resampling demonstrated stronger macro-level performance compared to flat classification.
- While hierarchical learning improves attack detection granularity, it introduces error propagation between stages and slightly reduces overall accuracy.
- However, the gain in macro-level performance outweighs the minor accuracy loss for security applications.
---
## Future Enhancements
- Perform feature importance analysis
- Tune the Stage 1 probability threshold instead of fixed 0.3
- Measure inference latency for real-time deployment

## Contact
For any inquiries, feel free to reach out via Email: saidililia555@gmail.com or visit my GitHub profile

