# Sunoco Gas Demand Forecasting

An academic forecasting project exploring weekly U.S. gasoline demand for inventory and supply planning.

## Report models and supporting files

The project report compares a simple time-trend regression, backward-selection regression, multiple regression models, gas-price × vehicle-miles interactions, ARIMAX with four covariates, and a seasonal-index model with vehicle miles and jobless claims.

Only three relevant Python notebooks are included. Their model names, predictor sets, and evaluation periods do not always match the report's final specifications, so they are supporting analysis rather than an exact reproduction of every reported result.

| File | Connection to the report |
| --- | --- |
| `Sunoco_Multiple_Regression_NEW.ipynb` | Multiple-regression exploration and diagnostics supporting the report's regression comparisons. Its Models A–F are not the same named models as the report's Models A–B. |
| `Sunoco_Stepwise_Regression_v2.ipynb` | Forward and backward selection, corresponding to the report's variable-selection approach. The selected predictors may differ from the final report model. |
| `Sunoco_Interactions_MLR.ipynb` | Interaction screening including gas price × vehicle miles and gas price × jobless claims, with weather predictors when available. |
| `Sunoco Training_complete_NEW.xlsx` | Shared input workbook read by all three notebooks; contains the `Target` sheet and source documentation. |
| `Sunoco_Training_Interactions.xlsx` | Workbook with the report's gas × VMT, gas × jobless claims, and holiday × daylight interactions, plus simple regression and earlier model outputs. |
| `Sunoco_Covariate_Model_VMT_JoblessClaims.xlsx` | Seasonal-index model with vehicle miles and jobless claims; cached 2025 validation MAPE is approximately 2.7468%. |
| `seasonal_index_model.xlsx` | Simplified seasonal-index workbook, using 2015–2019 and 2022–2024 training data. |
| `arimax_training_model.xlsx` | Demand/covariate panel, regression comparisons, an ARIMAX worksheet, and source documentation. |

The original report PDF is not included in the public repository. Workbooks are unchanged copies of the supplied files. Notebook code is preserved, with saved outputs and nonessential metadata removed.

## Files intentionally excluded

- `Sunoco_Ridge_Lasso_Model.ipynb`: ridge/lasso/elastic-net comparisons are not part of the report's model table.
- `Sunoco_Model_C_Refit_2022on.ipynb`: its 2022+ window differs from the restricted regression described in the report (2005–2024).
- `Sunoco_interactions_regression.ipynb`: an overlapping interaction-analysis alternative; one notebook is sufficient here.
- `Sunoco_Time_Series_Models.ipynb`: its ARIMAX uses gasoline price and vehicle miles, whereas the report uses gasoline price, jobless claims, cooling degree days, and a holiday indicator. Its additional benchmark models are also not the report's final comparison.
- `Sunoco_Model_Simplified (2).xlsx`: byte-identical to the simplified workbook already included.
- Ridge/lasso workbook and unrelated model variants.

## Run the notebooks

From the repository root:

```bash
python -m venv .venv
# macOS / Linux
source .venv/bin/activate
# Windows PowerShell: .venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
cd sunoco-gas-demand-forecasting
jupyter lab
```

Open any of the three notebooks and run its cells in order. They are independent analyses and all expect `Sunoco Training_complete_NEW.xlsx` in the same directory. The input workbook does not contain the holiday or daylight columns present in the interaction workbook; the interaction notebook detects available predictors and skips unavailable ones. It therefore cannot reproduce the report's full holiday/daylight specification from this input alone.

For Excel review, begin with `How It Works` in the simplified workbook, `Model Notes` in the covariate workbook, or `Reproducibility` / `Data Dictionary` in the larger workbooks. The exact Python fitting script for the report's four-covariate ARIMAX is still not supplied; the two-covariate time-series notebook is not a substitute.

## Report results and limitations

| Report result | Evaluation period | Reported value |
| --- | --- | ---: |
| Seasonal-index model with two covariates | 2025 validation | MAPE 2.7468% |
| ARIMAX with four covariates | 2025 validation | MAPE 3.2592% |
| Selected seasonal-index model | 2026 test period described in the report | MAPE 2.1677%; RMSLE 0.0287; RSE 249.7549 |

These are reported results, not benchmarks recomputed while preparing the repository. The report explicitly acknowledges 2025 contamination of the seasonal model, so the validation score is not a clean out-of-sample estimate. It also reports the separate 2026 test score above.

The notebooks use different preprocessing and validation choices: the stepwise notebook carries forward missing forecast inputs, the interaction notebook applies a 95% coverage threshold and uses earlier-year validation, and the regression notebook evaluates several alternative predictor sets. These differ from the report's stated 10% missingness cutoff and its 2025 validation split. Source relevance does not establish numerical agreement with the report.

All code cells passed syntax checks. Notebook execution and model metrics have not been independently verified during this upload.

## Data and attribution

Source organizations, URLs, coverage, and integration rules are recorded in workbook data dictionaries. This is a study of U.S. gasoline demand in a Sunoco business context, not verified Sunoco company sales. The report acknowledges extending an instructor's seasonal-model demonstration.
