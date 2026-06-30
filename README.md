# Adaptive Alarm Threshold Prediction in 4G Mobile Networks

This repository contains the implementation accompanying the paper:

> **Adaptive Alarm Threshold Prediction in 4G Mobile Networks Using a Percentile-Guided Deep Learning Framework with Interpretable Outputs**

## Overview

Mobile network operators typically configure alarm thresholds manually and keep them fixed for long periods of time. However, network behavior changes continuously according to traffic demand, time of day, and operational conditions. Static thresholds therefore lead to missed faults during busy periods and unnecessary alarm triggers during quiet periods.

This repository implements a machine learning framework for **adaptive alarm threshold prediction**. Instead of predicting whether a fault will occur, the proposed framework predicts the alarm thresholds themselves, allowing thresholds to automatically adapt to changing network conditions.

The repository includes implementations of:

- XGBoost baseline
- CNN-BiLSTM with Attention
- iTransformer baseline
- **PCTN (Percentile-Guided Contextual Threshold Network)**

along with preprocessing, exploratory analysis, anonymization, and statistical significance analysis.

---

# Repository Structure

```
.
├── Add prophet features.ipynb
├── Anonymizing.ipynb
├── EDA.ipynb
├── PreProcessing.ipynb
├── Statistical significance analysis.ipynb
├── Train model1 xgboost.py
├── Train model2 cnn bilstm.py
├── Train model4 iTransformer.ipynb
├── pctn.py
└── LICENSE
```

### File Description

| File | Description |
|------|-------------|
| `EDA.ipynb` | Exploratory data analysis and visualization |
| `Anonymizing.ipynb` | Data anonymization pipeline used before experimentation |
| `PreProcessing.ipynb` | Feature engineering and preprocessing |
| `Add prophet features.ipynb` | Generation of Prophet-based forecasting features |
| `Train model1 xgboost.py` | XGBoost baseline |
| `Train model2 cnn bilstm.py` | CNN-BiLSTM with attention baseline |
| `Train model4 iTransformer.ipynb` | iTransformer implementation |
| `pctn.py` | Proposed Percentile-Guided Contextual Threshold Network (PCTN) |
| `Statistical significance analysis.ipynb` | Wilcoxon signed-rank tests, Holm-Bonferroni correction, and effect size analysis |

---

# Dataset

The experiments were performed on an anonymized replica of operational data collected from a live 4G mobile network.

Dataset characteristics:

- **10,648 unique cells**
- **Three equipment vendors**
- **Nine geographic regions**
- **Ten sampled operational days**
- **Alarm snapshots every 10 minutes**

For privacy reasons, the original telecom dataset cannot be publicly released. But for research purpose can be given by contacting with any of the authors.

All identifiers have been anonymized and sensitive operational information removed before experimentation.

---

# Methodology

The complete workflow is:

1. Data anonymization
2. Feature engineering
3. Label derivation using percentile-guided thresholds
4. Model training
5. Model evaluation
6. Statistical significance analysis

The proposed PCTN predicts four adaptive alarm thresholds:

- Audit window duration
- Inactive time threshold
- Total fluctuation threshold
- Per-hour fluctuation threshold

---

# Requirements

The implementation uses Python 3.

Main libraries include:

- numpy
- pandas
- scikit-learn
- xgboost
- tensorflow
- keras
- pytorch
- matplotlib
- scipy
- prophet

Install dependencies using:

```bash
pip install numpy pandas scikit-learn xgboost tensorflow torch matplotlib scipy prophet
```

---

# Reproducing the Experiments

The experiments can be reproduced using the following workflow.

## Step 1

Run preprocessing.

```
PreProcessing.ipynb
```

## Step 2

(Optional)

Generate Prophet features.

```
Add prophet features.ipynb
```

## Step 3

Train baseline models.

```
Train model1 xgboost.py
Train model2 cnn bilstm.py
Train model4 iTransformer.ipynb
```

## Step 4

Train the proposed model.

```
pctn.py
```

## Step 5

Evaluate statistical significance.

```
Statistical significance analysis.ipynb
```

---

# Statistical Analysis

The paper reports statistical significance using:

- Wilcoxon signed-rank test
- Holm-Bonferroni correction
- Standardized Wilcoxon effect sizes

These analyses can be reproduced using:

```
Statistical significance analysis.ipynb
```

---

# Results

PCTN achieved:

- Best overall average R² across the four prediction targets
- Competitive predictive accuracy with substantially fewer parameters than iTransformer
- Interpretable threshold generation through its probabilistic output heads and dynamic alpha mechanism

Complete experimental results are available in the accompanying manuscript.

---

# Citation

If you use this repository, please cite:

```
@article{roy2026adaptive,
  title={Adaptive Alarm Threshold Prediction in 4G Mobile Networks Using a Percentile-Guided Deep Learning Framework with Interpretable Outputs},
  author={Roy, Ayon and Others},
  journal={Under Review},
  year={2026}
}
```

---

# License

This project is released under the MIT License.

See the `LICENSE` file for details.
