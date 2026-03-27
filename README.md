# COMP3314 Machine Learning Challenge – Image Classifier

[![Run Notebook](https://github.com/NaughtyChas/COMP3314-ML-Challenge/actions/workflows/run_notebook.yml/badge.svg)](https://github.com/NaughtyChas/COMP3314-ML-Challenge/actions/workflows/run_notebook.yml)

A starter repository for the COMP3314 Kaggle image-classification competition.

---

## Rules

| Rule | Details |
|------|---------|
| ❌ No neural networks | CNNs, RNNs, Transformers, etc. are **not** allowed |
| ❌ No external data | Only the provided competition dataset may be used |
| ❌ No pre-trained models | All models must be trained from scratch on the competition data |
| ❌ No plagiarism | Code and predictions must be your own |

---

## Approach

Classical machine-learning pipeline:

1. **Feature extraction** – three complementary feature families:
   - **HOG** (Histogram of Oriented Gradients) – captures shape & edge structure
   - **LBP** (Local Binary Patterns) – captures texture information
   - **Colour histograms** – captures global colour distribution
2. **Dimensionality reduction** – PCA (retaining 95% of variance)
3. **Model comparison** via stratified k-fold cross-validation:
   - SVM with RBF kernel
   - Random Forest
   - Gradient Boosting
   - k-Nearest Neighbours
4. **Best model** retrained on the full training set → submission CSV

---

## Repository Structure

```
.
├── image_classifier.ipynb   # Main notebook (run this)
├── requirements.txt         # Python dependencies
├── .github/
│   └── workflows/
│       └── run_notebook.yml # CI/CD: executes the notebook on every push/PR
└── data/                    # Place competition data here (git-ignored)
    ├── train/
    │   ├── class_a/
    │   └── class_b/
    ├── test/
    └── sample_submission.csv
```

---

## Quick Start

```bash
# 1. Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Place competition data in data/ (see structure above)

# 4. Launch the notebook
jupyter notebook image_classifier.ipynb
```

---

## CI/CD

Every push and pull request triggers the **Run Notebook** GitHub Actions workflow
([`.github/workflows/run_notebook.yml`](.github/workflows/run_notebook.yml)).

The workflow:
1. Installs all Python dependencies.
2. Generates a tiny synthetic dataset so the notebook can execute without real data.
3. Runs the notebook end-to-end with `jupyter nbconvert --execute`.
4. Uploads the executed notebook as a downloadable artifact (retained for 14 days).
