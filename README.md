# Data Mining and Analytics

This repository contains selected coursework and applied projects from the **Data Mining and Analytics (COU 08104)** module at the Dar es Salaam Institute of Technology. The assignments demonstrate an end-to-end workflow for turning raw data into useful evidence: data preparation, exploratory analysis, statistical modelling, unsupervised learning, pattern discovery, recommendation, and interpretation.

## Highlights

- Exploratory data analysis and correlation analysis
- Ordinary least squares and logistic regression
- Statistical significance testing and model comparison
- Forward stepwise feature selection
- Categorical encoding and missing-value imputation
- Principal Component Analysis (PCA) of financial returns
- Frequent-itemset discovery and association-rule mining
- Evaluation with support, confidence, lift, and leverage
- Item-based collaborative filtering with cosine similarity
- Reproducible synthetic experiments and documented findings

## Assignments

| Assignment | Focus | Main techniques |
| --- | --- | --- |
| [Assignment 02](Assignment02/README.md) | Regression, classification, and dimensionality reduction | OLS regression, logistic regression, PCA, correlation analysis, model evaluation |
| [Assignment 04](Assignment04/README.md) | Association mining and recommendation systems | Apriori, association rules, transaction transformation, cosine similarity, collaborative filtering |

## Assignment 02: Statistical Learning and PCA

[Assignment 02](Assignment02/README.md) covers three applied analyses:

- **Diabetes regression:** investigates multicollinearity, fits a full OLS model, performs forward feature selection, and compares model performance.
- **Titanic classification:** estimates survival probabilities and fits logistic regression using passenger class, sex, and age.
- **Dow Jones PCA:** transforms daily stock prices into returns, analyzes eigenvalues and eigenvectors, and interprets principal components as market and sector-related factors.

The notebook uses Python libraries including pandas, NumPy, Matplotlib, Seaborn, scikit-learn, statsmodels, SciPy, and yfinance. The PCA section requires an internet connection to retrieve market data.

## Assignment 04: Association Rules and Recommendations

[Assignment 04](Assignment04/README.md) applies unsupervised learning to transactional and synthetic data:

- Measures support for faceplate itemsets and mines rules with Apriori.
- Converts Charles Book Club purchases into a binary incidence matrix.
- Compares support, confidence, lift, and leverage when interpreting associations.
- Uses seeded synthetic transactions to examine patterns that may occur by chance.
- Builds an item-based collaborative-filtering model with Surprise and cosine similarity.

The notebook uses pandas, NumPy, mlxtend, scikit-surprise, and Jupyter. Random experiments use seed `0` for repeatability.

## Repository Structure

```text
.
├── Assignment02/
│   ├── data/
│   ├── findings/
│   ├── instructions/
│   ├── main.ipynb
│   ├── README.md
│   └── requirements.txt
├── Assignment04/
│   ├── data/
│   ├── instructions/
│   ├── main.ipynb
│   ├── README.md
│   └── requirements.txt
└── README.md
```

Each assignment is self-contained and includes its own notebook, datasets, requirements, and assignment-specific documentation where applicable.

## Running the Projects

Open the assignment directory you want to explore, create a Python virtual environment, and install its dependencies:

```bash
cd Assignment02  # or Assignment04
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
jupyter notebook main.ipynb
```

Run each notebook from top to bottom. Dataset paths are relative to the corresponding assignment directory. Assignment 02 may need internet access for the Yahoo Finance data retrieval described in its README.

## Reproducibility and Interpretation

The notebooks document their data sources, dependencies, and random seeds. Results that depend on external market data may change when the data provider updates its historical records. Association rules and PCA components describe patterns in the available data; they should be interpreted as analytical evidence rather than proof of causation.

## Portfolio Value

Together, these assignments show the ability to work across supervised and unsupervised data-mining tasks, select appropriate representations for different datasets, evaluate models and discovered patterns, and communicate technical findings in a reproducible notebook-based workflow.
