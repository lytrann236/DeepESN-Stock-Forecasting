# DeepESN Stock Price Forecasting for Vietnamese Stocks

## Overview

This project proposes a **Deep Echo State Network (DeepESN)** architecture for forecasting stock closing prices in the Vietnamese stock market.

The study evaluates DeepESN against several baseline models, including:

* ARIMA
* LSTM
* Random Forest
* Standard ESN (Echo State Network)

Experiments are conducted on multiple Vietnamese stocks from different sectors to assess forecasting accuracy, robustness, and computational efficiency.

---

## Key Features

* Multi-layer DeepESN architecture
* Hyperparameter optimization using Grid Search
* Multi-seed evaluation for robustness
* Comparison with traditional and machine learning baselines
* Time series preprocessing:

  * Moving average smoothing
  * First-order differencing
  * Min-Max normalization
* Walk-forward validation
* Statistical analysis and visualization
* Ablation study on reservoir depth
* Sensitivity analysis on smoothing windows
* Explainability analysis using Permutation Importance
* Stationarity verification using Augmented Dickey-Fuller (ADF) test

---

## Dataset

The project uses historical daily stock data from the Vietnamese stock market.

Example stocks:

| Ticker | Company               |
| ------ | --------------------- |
| TCB    | Techcombank           |
| CTG    | VietinBank            |
| CTS    | VietinBank Securities |
| FPT    | FPT Corporation       |
| PAN    | PAN Group             |
| DIG    | DIC Corp              |
| MSN    | Masan Group           |
| TPB    | TPBank                |
| DBC    | Dabaco                |
| SAB    | Sabeco                |

Required columns:

* Date
* Open
* High
* Low
* Close

Supported formats:

* Excel (.xlsx)
* CSV (.csv)

---

## Methodology

### 1. Data Preprocessing

The raw closing price series undergoes:

1. Missing value handling
2. Moving average smoothing
3. First-order differencing
4. Train/Validation/Test split

Dataset split:

* Training: 80%
* Validation: 10%
* Testing: 10%

---

### 2. DeepESN Architecture

The proposed DeepESN consists of:

* Multiple stacked reservoir layers
* Sparse recurrent connections
* Spectral radius control
* Ridge regression readout layer

Activation function:

```python
ReLU
```

Reservoir parameters include:

* Number of reservoirs
* Number of layers
* Spectral radius
* Sparsity
* Ridge regularization coefficient

---

### 3. Hyperparameter Optimization

Grid Search is performed over:

```text
n_reservoir      : [40, 45, 50, 55]
n_layers         : [2, 3]
spectral_radius  : [0.70, 0.72, 0.73, 0.74, 0.75]
sparsity         : [0.07, 0.08, 0.09, 0.10, 0.12]
ridge_alpha      : [5e-4, 7e-4, 1e-3, 2e-3, 3e-3, 4e-3]
```

Models are evaluated using validation MAE.

---

## Evaluation Metrics

The following metrics are reported:

* MAE (Mean Absolute Error)
* RMSE (Root Mean Squared Error)
* MAPE (Mean Absolute Percentage Error)
* R² Score

Multi-seed experiments are conducted using:

```python
[0, 42, 123, 456, 789, 1234]
```

to ensure robustness.

---

## Additional Experiments

### Ablation Study

Comparison between:

* ESN (1 reservoir layer)
* DeepESN (2 layers)
* DeepESN (3 layers)

to investigate the impact of reservoir depth.

### Sensitivity Analysis

Smoothing window sizes: 3, 5, 7, 10

are tested to analyze preprocessing effects.

### Explainability

Permutation Importance is used to identify influential lag features contributing to predictions.

### Stationarity Analysis

ADF tests are performed after differencing to verify stationarity assumptions.

---

## Project Structure

```text
.
├── DeepESN_Forecasting.ipynb
├── datasets/
│   ├── TCB.xlsx
│   ├── CTG.csv
│   ├── CTS.csv
│   └── ...
├── figures/
├── results/
└── README.md
```

---

## Installation

Clone the repository:

```bash
git clone https://github.com/yourusername/deepesn-stock-forecasting.git
cd deepesn-stock-forecasting
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Main Dependencies

```text
numpy
pandas
matplotlib
scikit-learn
statsmodels
tensorflow
openpyxl
scipy
```

---

## Run

Open the notebook:

```bash
jupyter notebook DeepESN_Forecasting.ipynb
```

or

```bash
jupyter lab
```

Execute all cells sequentially.

---

## Results

The proposed DeepESN consistently demonstrates:

* Lower forecasting error than traditional ESN
* Competitive performance compared with LSTM
* Stable predictions across multiple random seeds
* Efficient training compared to deep recurrent neural networks

---

## Research Contribution

This work explores the application of Deep Echo State Networks to Vietnamese stock market forecasting and provides:

* A comprehensive DeepESN implementation
* Extensive hyperparameter tuning
* Multi-stock evaluation
* Explainability analysis
* Robustness and sensitivity studies


