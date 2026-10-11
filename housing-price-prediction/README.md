# Housing Price Prediction

**Author:** Harshini Chinta  
**Type:** Academic project  
**Tools:** Python, pandas, NumPy, seaborn, Matplotlib, SciPy, pingouin, statsmodels, scikit-learn

## Goal

Explore a Kaggle housing dataset and build a linear regression model relating residential sale prices to property characteristics.

## Analysis

The notebook explores and cleans housing variables, handles missing values, creates indicator variables, and investigates relationships with `SalePrice`. It includes transformations, outlier capping, and standardization. The final regression uses living area, basement area, neighborhood, kitchen quality, garage characteristics, year built, and other selected predictors.

The analysis examines residuals and variance inflation factors to assess model assumptions and collinearity.

## Files

- `housing_analysis.ipynb`: Original coursework analysis, with saved outputs removed and one leading indentation error corrected in a scatterplot cell.
- `train.csv`: User-supplied housing training data, with 1,460 rows and 81 columns.

## Run locally

From the portfolio root:

```bash
python -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
cd housing-price-prediction
jupyter lab housing_analysis.ipynb
```

Run the notebook in order with `train.csv` in the same directory.

## Evaluation and limitations

This notebook documents a coursework regression analysis. It does not establish a held-out predictive benchmark, so training fit and diagnostic plots should not be treated as verified performance on new homes. The target and several predictors are transformed; model outputs are not necessarily expressed in sale-price dollars.

Two living-area values are manually changed after examining residuals in the original analysis. A stronger future evaluation would reserve a test set before preprocessing, learn transformations on training data only, and compare the model with a baseline using MAE, RMSE, and R-squared.

## Data attribution

The provided data has the structure of Kaggle's **House Prices: Advanced Regression Techniques** training dataset, based on Ames housing data. The original notebook describes it as a Kaggle project. Dataset redistribution terms are not included in the supplied files; consult the original dataset terms before republishing the data elsewhere.
