# Hierarchical vs Flat Machine Learning for Intrusion Detection

## Overview
This research project compares **Flat** and **Hierarchical** machine learning approaches for Intrusion Detection Systems (IDS) using the **UNSW-NB15 dataset**.

We investigate whether decomposing attack detection into a two-stage pipeline improves:

- Rare attack detection
- Macro F1-score
- Robustness under class imbalance
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
- SMOTENC + Undersampling


---

### Hierarchical Model

#### Stage 1 — Binary Detection

- XGBoost
- Attack vs Normal
- Class-weighted training
- Threshold-based prediction (default = 0.3)


---

#### Stage 2 — Attack Refinement

Triggered only if Stage 1 predicts **Attack**

- Trained only on attack samples
- RandomForest
- Hyperparameter tuning via Optuna
- Adaptive resampling (target_count)
- SMOTENC balancing


## Technologies Used
- **Python**
- **Scikit-Learn**
- **xgboot**
- **imblearn**
- **Pandas & NumPy**
- **Optuna** (for advanced optimization)

## Results & Insights
### Performance Comparison

| Model         | Accuracy | Macro F1 | Weighted F1 | Attack Recall |
|--------------|----------|----------|------------|--------------|
| Flat         | 0.87     | 0.60     | 0.87       | 0.58         |
| Hierarchical | 0.85     | 0.71     | 0.90       | 0.76         |

## Installation & Usage
1. Clone the repository:
   ```sh
   git clone https://github.com/saidililia/Swarm-Optimization.git
   ```
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
3. Run the main script:
   ```sh
   python main.py
   ```

## Future Enhancements
- Implement deep learning models (e.g., LSTMs, CNNs) for better performance.
- Experiment with additional feature selection techniques.

## Contact
For any inquiries, feel free to reach out via Email: saidililia555@gmail.com or visit my GitHub profile
