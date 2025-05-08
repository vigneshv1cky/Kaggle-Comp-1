# Russian Car Plates Prices Prediction

## Overview

This repository contains code and documentation for the Russian Car Plates Prices Prediction competition on Kaggle. Participants build machine learning models to predict the sale price of custom Russian vehicle registration plates using historical offers data spanning 2021–2025. The goal is to minimize the Symmetric Mean Absolute Percentage Error (SMAPE) on unseen test plates.

## Competition Details

* **Host:** Solomon Andryushenko
* **Timeline:** Ongoing (closes in 22 days)
* **Participants:** 1,632 entrants, 550 active participants, 495 teams
* **Prize Pool:** \$50 (1st: \$25, 2nd: \$15, 3rd: \$10)
* **Metric:** SMAPE (lower is better)

## Dataset

The dataset includes:

* **id:** Unique identifier for each listing
* **plate:** Vehicle registration plate (3 letters + 3 digits + region code)
* **price:** Listed sale price (RUB)
* **date:** Date of listing (YYYY-MM-DD)
* **letter\_code, serial, region, region\_name:** Extracted components
* **flags:** Government affiliation, symbolic meanings (e.g., repeated letters/digits), advantage and forbidden codes

### Data Files

* `train.csv` – Historical offers with prices
* `test.csv` – Plates for which you must predict `price`
* `submission_sample.csv` – Example submission format

## Feature Engineering

Participants may consider:

* **Plate composition:** Letter patterns, numeric patterns, region code
* **Government codes:** Identifying government or special plates
* **Symbolic value:** Palindromes, repeated characters, unique patterns

## Modeling Approach

A typical workflow includes:

1. **Data preprocessing** – Parse `plate` into structured features, impute missing values, clip outliers
2. **Feature generation** – Create time-based features (e.g., days since first listing), encode categorical variables
3. **Model selection** – Algorithms like Random Forests, Gradient Boosting (XGBoost, LightGBM), or neural networks
4. **Hyperparameter tuning** – Cross-validation and grid or Bayesian search
5. **Ensembling** – Blend multiple models to improve robustness

## Evaluation

Predictions are scored using SMAPE:

```
SMAPE = 100% * (2 * |y_pred - y_true|) / (|y_pred| + |y_true|)
```

A lower SMAPE indicates a more accurate model, accounting fairly for different price scales.

## Submission

1. Generate a CSV file `submission.csv` with columns `id,price`.
2. Ensure no header or index column beyond the specified two columns.
3. Upload on Kaggle under the competition page: [https://kaggle.com/competitions/russian-car-plates-prices-prediction](https://kaggle.com/competitions/russian-car-plates-prices-prediction)

## Citation

If you use this work, please cite:

> Solomon Andryushenko. Russian Car Plates Prices Prediction. [https://kaggle.com/competitions/russian-car-plates-prices-prediction](https://kaggle.com/competitions/russian-car-plates-prices-prediction), 2025.
