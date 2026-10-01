# Data Mining and Analytics: Assignment 2

This project demonstrates practical data mining and statistical analysis using Python. It was completed for the **Data Mining and Analytics (COU 08104)** module at the Dar es Salaam Institute of Technology.

The analysis covers three applied problems:

- Diagnosing multicollinearity and building linear regression models for diabetes progression.
- Estimating Titanic survival probabilities and fitting a logistic regression classifier.
- Applying Principal Component Analysis (PCA) to daily returns from 30 Dow Jones constituent stocks.

## Portfolio Highlights

This work demonstrates experience with:

- Exploratory data analysis and correlation matrices.
- Heat-map and statistical visualization with Matplotlib and Seaborn.
- Ordinary Least Squares (OLS) regression using `statsmodels`.
- Statistical significance testing with coefficient p-values.
- Forward stepwise feature selection.
- Categorical encoding and median imputation.
- Logistic regression evaluation with a confusion matrix and classification accuracy.
- Eigenvalue and eigenvector analysis for PCA.
- Financial time-series retrieval with `yfinance`.
- Explained variance analysis, scree plots, PCA loadings, projections, and Euclidean distance.

## Analytical Work

### 1. Diabetes Regression

The diabetes dataset contains 442 observations, ten explanatory variables, and a quantitative disease-progression target.

The analysis:

1. Loads the dataset and visualizes correlations among explanatory variables.
2. Fits a multivariate OLS model with all ten predictors and an intercept.
3. Reviews mean squared error, adjusted $R^2$, coefficient p-values, and the model condition number.
4. Implements forward selection based on the smallest available p-value below a significance threshold of `0.05`.
5. Compares the full model with the selected-feature model.

The recorded findings show a strong positive correlation of approximately `0.90` between `S1` and `S2`, indicating potential multicollinearity. The `S3`/`S4` relationship is also notable at approximately `-0.74`. The fitted model has a large condition number of approximately `7.24e+03`, supporting further investigation of numerical stability and correlated predictors.

### 2. Titanic Survival Classification

The Titanic analysis uses passenger class, encoded sex, and age to model survival.

The workflow:

- Calculates the overall survival probability.
- Groups passengers by sex, age group, and passenger class to produce survival probabilities.
- Encodes the categorical sex variable and imputes missing ages with the median.
- Fits a scikit-learn logistic regression model.
- Fits a `statsmodels` logit model to inspect coefficient significance.
- Evaluates predictions with a confusion matrix and classification accuracy.

The recorded coefficient estimates were approximately:

| Parameter | Estimate | Significance |
| --- | ---: | --- |
| Passenger class | `-1.0691` | Statistically significant at `0.05` |
| Encoded sex | `-2.4984` | Statistically significant at `0.05` |
| Age | `-0.0318` | Statistically significant at `0.05` |

These results illustrate how passenger class, sex, and age contribute to the estimated probability of survival while also showing the difference between a continuous-output regression model and a categorical-output classification model.

### 3. PCA of Dow Jones Stock Returns

The notebook downloads daily prices for 30 Dow Jones constituents over the period from 1 January 2020 to 1 January 2021. Closing prices are converted into daily percentage returns, and the returns correlation matrix is decomposed into eigenvalues and eigenvectors.

The analysis includes:

- Construction of the PCA weight matrix from the first two eigenvectors.
- Bar charts of stock weights for PC1 and PC2.
- A scree plot and cumulative explained-variance analysis.
- A two-dimensional projection of the return observations.
- Distance-based investigation of unusual observations and stock loadings.

The recorded interpretation is that the first principal component behaves similarly to a broad market factor because its weights capture common movement across the constituent stocks. The second component is interpreted as a more specific factor that can reflect differences between sectors or individual stocks.

## Repository Contents

```text
Assignment02/
├── data/
│   ├── Diabetes_Data.xlsx
│   └── titanic3.csv
├── findings/
│   └── main.pdf
├── instructions/
│   └── assignment02.pdf
├── main.ipynb
├── requirements.txt
└── README.md
```

## Tools and Libraries

- Python
- Jupyter Notebook
- pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- statsmodels
- SciPy
- openpyxl
- yfinance

## Running the Notebook

From the `Assignment02` directory:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pip install yfinance
jupyter notebook main.ipynb
```

The PCA section requires an internet connection because historical market data is retrieved from Yahoo Finance. The downloaded data can change as data-provider responses and ticker histories change, so PCA outputs may vary slightly between runs.

## Reproducibility Notes

- The datasets are stored in the `data/` directory.
- The checked-in `requirements.txt` does not currently list `yfinance`; it is installed separately in the setup commands above.
- The explanatory findings are available in [findings/main.pdf](findings/main.pdf), while the assignment brief is available in [instructions/assignment02.pdf](instructions/assignment02.pdf).

## Learning Outcomes

This project strengthened my ability to move from raw data to interpretable analytical results: inspect relationships, diagnose modelling risks, select useful predictors, quantify classification performance, reduce dimensionality, and communicate findings with statistical evidence and visualizations.