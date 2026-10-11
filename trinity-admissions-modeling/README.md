# Trinity Admissions Modeling

**Author:** Harshini Chinta  
**Type:** Academic project using course-provided materials  
**Tools:** Python, pandas, NumPy, Matplotlib, scikit-learn

## Goal

Prepare admissions data and compare classification models predicting whether admitted students accept their offers. The data-preparation notebooks describe entry terms from Fall 2017 through Fall 2021.

## Workflow

1. Prepare the training subset: inspect missing values, consolidate categories, derive variables, and export `cleaneddftrain.csv`.
2. Prepare the test subset and export `cleaneddftest.csv`.
3. Build decision trees, use cost-complexity pruning, and compare random forests.
4. Evaluate accuracy, precision, recall, F1, Cohen's kappa, and out-of-bag accuracy.

The original preparation notebooks contain instructor guidance and student work; this portfolio does not claim sole authorship of the course starter materials.

## Files

- `01_prepare_training.ipynb`
- `02_prepare_test.ipynb`
- `03_modeling.ipynb`

Saved outputs and nonessential notebook metadata have been removed. Student-level records, `TU.csv`, and generated admissions CSVs are excluded.

## Results recorded in the original notebook

These are saved coursework results, not newly reproduced benchmarks. They refer to the later models in the notebook.

| Model | Test accuracy | Test precision | Test recall | Test F1 | Test Cohen's kappa |
| --- | ---: | ---: | ---: | ---: | ---: |
| Pruned decision tree | 0.820 | 0.620 | 0.536 | 0.575 | 0.461 |
| Random forest | 0.829 | 0.675 | 0.480 | 0.561 | 0.459 |

The random forest's recorded out-of-bag accuracy was 0.830. Its near-perfect training scores suggest that generalization should be assessed carefully.

## Run with authorized data

The original `TU.csv` was not supplied with this portfolio, so the admissions workflow cannot be executed from these files alone. Do not substitute the housing `train.csv`.

Install dependencies using the portfolio's `requirements.txt`, then launch Jupyter from this project directory. Place an authorized `TU.csv` here and run the three notebooks in the listed order. The preparation notebooks write the filenames expected by the modeling notebook. Admissions CSVs are ignored by Git.

## Methodological limitations

The notebooks preserve the original coursework code. Before interpreting results as a reliable deployment benchmark:

- Fit categorical mappings, imputation rules, and grouping thresholds on training data and reuse them on validation and test data. The original notebooks process subsets separately.
- The encoding helper uses `LabelEncoder`, although its original comment describes one-hot encoding.
- The test-preparation notebook uses the variable name `TUtrain` for the subset selected with `train-test == 'test'`; this name is confusing but preserved.
- Review sensitive demographic features and ensure predictors are available at the time an enrollment prediction would be made.

The original training-preparation notebook also contained a stale saved `NameError` in an empty final cell. Its outputs were cleared; all published code cells passed syntax checks, but execution has not been verified without the underlying data.
