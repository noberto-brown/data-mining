# Data Mining and Analytics: Assignment 04

This project applies association-rule mining and item-based collaborative filtering to transactional and synthetic data. It demonstrates practical experience with data preparation, frequent-itemset discovery, rule evaluation, and recommendation generation in Python.

## Assignment Context

- **Module:** Data Mining and Analytics (COU 08104)
- **Assignment:** 04
- **Registration number:** 230242452779
- **Primary notebook:** [`main.ipynb`](main.ipynb)
- **Python kernel:** Python 3.10.21

## Learning Objectives

The notebook implements the required tasks from the assignment brief:

1. Measure support for a faceplate itemset.
2. Apply the Apriori algorithm to faceplate transactions and interpret association rules.
3. Prepare Charles Book Club purchase data as a binary incidence matrix and mine purchase associations.
4. Compare support, confidence, lift, and leverage when interpreting rules.
5. Generate repeatable synthetic transactions and examine association rules that may arise by chance.
6. Build an item-based collaborative-filtering model with cosine similarity using Surprise.

## Project Structure

```text
Assignment04/
├── main.ipynb
├── requirements.txt
├── README.md
├── data/
│   ├── CharlesBookClub.csv
│   └── Faceplate.csv
└── instructions/
```

## Datasets

### Faceplate transactions

`data/Faceplate.csv` contains one row per transaction and binary purchase indicators for six faceplate colors: `Red`, `White`, `Blue`, `Orange`, `Green`, and `Yellow`. The `Transaction` column identifies each transaction and is excluded from itemset mining.

### Charles Book Club

`data/CharlesBookClub.csv` contains customer-level purchase information. The notebook removes identifiers, demographic fields, recency/frequency/monetary fields, derived code columns, and other non-book fields. The remaining 11 book-category columns are converted to binary values: values greater than zero indicate a purchase.

## Methods Implemented

### Association rules

The notebook uses `mlxtend.frequent_patterns` to:

- Generate frequent itemsets with `apriori`.
- Generate rules with `association_rules`.
- Sort rules by descending lift.
- Report antecedents, consequents, support, confidence, lift, and leverage.
- Identify high-support, high-lift, and low-confidence rules for interpretation.

The main thresholds are:

| Analysis | Minimum support | Minimum confidence | Reported rules |
| --- | ---: | ---: | ---: |
| Faceplates | 20% | 50% | Top 6 by lift |
| Book purchases | 5% | 50% | Top 25 by lift |
| Synthetic transactions | 4% (2 of 50) | 70% | Top 6 by lift |

The synthetic transactions use `random.seed(0)` so that the generated binary matrix and resulting analysis are reproducible.

### Item-based collaborative filtering

The notebook creates 5,000 synthetic ratings with:

- `userID` values from 0 to 999
- `itemID` values from 0 to 99
- ratings from 1 to 5
- `random.seed(0)` for repeatability

The ratings are loaded into Surprise, split into training and test sets, and modeled with `KNNBasic` using cosine similarity and `user_based=False`. The model evaluates held-out ratings and uses nearest item neighbors to produce item recommendations for users represented in the predictions.

## Key Concepts

- **Support:** The proportion of transactions containing an itemset.
- **Confidence:** The proportion of transactions containing the antecedent that also contain the consequent.
- **Lift:** How much more often the antecedent and consequent occur together than would be expected if they were independent.
- **Leverage:** The difference between the observed joint support and the support expected under independence.

High lift can identify strong relationships, but it should be considered together with support. A rare rule may be efficient while affecting too few transactions to be useful operationally.

## Setup

Create and activate a Python 3.10.21 environment, then install the pinned environment dependencies:

```bash
python3.10 -m venv .venv
source .venv/bin/activate
python --version
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```

The project uses, among others, `pandas`, `numpy`, `mlxtend`, `scikit-surprise`, and `jupyter`/`ipykernel`.

## Running the Notebook

From the project directory:

```bash
jupyter notebook main.ipynb
```

Select the Python 3.10.21 kernel and run the cells from top to bottom. The notebook expects the dataset paths to remain relative to the project root:

```python
data/Faceplate.csv
data/CharlesBookClub.csv
```

All imports are grouped at the beginning of the notebook, before the analysis cells, as required by the assignment brief.

## Portfolio Relevance

This project shows an end-to-end analytical workflow: loading real transactional data, transforming raw fields into mining-ready representations, applying unsupervised pattern-discovery methods, evaluating competing rule-quality measures, creating reproducible synthetic experiments, and implementing a recommendation model for unseen ratings.

The results should be interpreted as analytical evidence rather than causal conclusions. In particular, association rules describe co-occurrence and do not by themselves prove that purchasing one item causes another purchase.

## Reproducibility Notes

- Random experiments use seed `0`.
- Dataset files are included in the `data/` directory.
- The notebook is intended to be executed in order because later cells use variables created earlier.
- `requirements.txt` records the Python environment used for the analysis.