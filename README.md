# AI-Based Fraud Detection in Mobile Transactions (PaySim)

This repository compares **Isolation Forest** (unsupervised anomaly detection) and **Random Forest** (supervised classification with class balancing) to detect fraudulent mobile money transactions using the **PaySim** dataset.

> **Key finding:** On balanced data, Random Forest achieves strong results (≈97.4% accuracy, 96.7% precision, 98.3% recall, 97.5% F1), outperforming Isolation Forest which shows high overall accuracy but poor fraud recall on imbalanced data.

---

## 📁 Repository Structure

```
.
├── notebooks/
│   └── x23302372.ipynb              # End-to-end EDA, preprocessing, modeling
├── src/
│   └── train_and_evaluate.py        # Auto-generated consolidation of notebook code cells
├── data/
│   ├── raw/                         # Put original PaySim CSV here (not versioned)
│   └── processed/                   # Generated balanced/cleaned datasets
├── reports/
│   └── x23302372.pdf                # Project report
├── slides/
│   └── x23302372.pptx               # Slide deck
├── requirements.txt
├── environment.yml
├── LICENSE
└── .github/workflows/ci.yml
```

> **Note:** The dataset is not committed. Download it locally and place it under `data/raw/`.

---

## 🚀 Quickstart

### 1) Clone and set up
```bash
git clone <your-repo-url>.git
cd fraud-detection-paysim-github
python -m venv .venv && source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

> Or with Conda:
```bash
conda env create -f environment.yml
conda activate fraud-detection-paysim
```

### 2) Get the data
Download the PaySim dataset from Kaggle and place it as:
```
data/raw/paysim.csv
```
Dataset: https://www.kaggle.com/datasets/ealaxi/paysim1

### 3) Run the notebook
```bash
jupyter notebook notebooks/x23302372.ipynb
```

### 4) (Optional) Run the script
The `src/train_and_evaluate.py` script is an auto-generated consolidation of code cells.
You may need to adapt paths and parameters:

```bash
python src/train_and_evaluate.py
```

---

## 🧠 Methods

- **Isolation Forest (Unsupervised):** Trained on imbalanced data. High overall accuracy but very low fraud recall/precision due to skew.
- **Random Forest (Supervised + Class Balancing via Downsampling):** Trained on class-balanced data. Strong precision/recall and F1.

**Reported Metrics (from the accompanying report):**
- Isolation Forest (imbalanced): ~99.79% accuracy, but very low precision/recall for fraud.
- Random Forest (balanced): **97.38% accuracy**, **96.7% precision**, **98.32% recall**, **97.51% F1**.

> Tip: You can also experiment with alternative balancing (e.g., `SMOTE`, `class_weight="balanced"`), additional models, and threshold tuning.

---

## 📊 Reproducing Results

1. Ensure the column names and encodings in your CSV match the notebook expectations.
2. Execute the notebook cells in order.
3. Save generated artifacts (e.g., confusion matrices, performance plots) into `reports/`.

---

## 📜 Citation

If you use this repository, please cite:
- Liu, Ting, Zhou. **Isolation Forest**. ICDM 2008. DOI: https://doi.org/10.1109/icdm.2008.1  
- PaySim Dataset: https://www.kaggle.com/datasets/ealaxi/paysim1

---

## 🛡️ License

Released under the MIT License. See `LICENSE` for details.