# Sunoco Gas Demand Forecasting

**Author:** Harshini Chinta  
**Type:** Academic forecasting project; no claim of employment or commissioned work for Sunoco  
**Tools:** Microsoft Excel, regression, seasonal indices, ARIMAX

## Business question

How can weekly U.S. gasoline demand be forecast to support inventory planning, supply decisions, and short-term business goals?

## Files

| File | Contents |
| --- | --- |
| `seasonal_index_model.xlsx` | Trend estimation, weekly seasonal indices, regression with vehicle miles and jobless claims, and a 2025 forecast worksheet |
| `arimax_training_model.xlsx` | Weekly demand and covariate panel, regression comparisons, an ARIMAX(1,1,1) worksheet, a data dictionary, and reproducibility notes |

The workbooks are unchanged copies of the uploaded files. The original course report is not published here; the methodology and limitations below summarize it.

## Approach

The report describes screening variables with more than 10% missing values, comparing several regression and time-series approaches, and considering external drivers such as gasoline prices, vehicle miles, jobless claims, weather, daylight, and holiday indicators.

The simplified workbook uses training data from 2015–2019 and 2022–2024, excluding 2020–2021. It estimates a trend, calculates weekly seasonal indices, fits a regression to deseasonalized demand, and applies the seasonal indices to forecasts.

## Results and limitations

The report's comparison table records a 2.7468% MAPE for a seasonal-index model with two covariates and a 3.2592% MAPE for an ARIMAX model with four covariates. Its conclusion separately reports 2.167% MAPE for the final model. These values refer to the original report and have not been recomputed here.

The report explicitly states that 2025 data contaminated the seasonal model. These errors must therefore not be presented as an unbiased held-out benchmark. The different MAPE values should be reconciled before quoting one headline result.

The resume mentions ridge, lasso, and ARIMAX with two covariates; the supplied report and workbooks describe a different set of model comparisons. This portfolio summarizes the supplied artifacts without inventing missing ridge or lasso implementation files.

## Review locally

Open the `.xlsx` files in Microsoft Excel. For the simplified model, read the `How It Works` sheet, then review training data, seasonal indices, regression, and forecast sheets in order. For the larger workbook, begin with `Reproducibility`, `Data Dictionary`, and `ARIMAX(1,1,1) Model`.

The ARIMAX worksheet states that fitted parameter estimates were exported from Python statsmodels. The original fitting script is not included, so the full estimation procedure cannot be reproduced from the uploaded files alone. Excel can display and recalculate the existing workbook formulas.

## Sources and interpretation

Source organizations, URLs, coverage, and integration rules are recorded in the larger workbook's `Data Dictionary`. This is an analysis of U.S. gasoline demand in a Sunoco business context; the target should not be described as verified Sunoco company sales. The original report acknowledges extending an instructor's seasonal-model demonstration.
