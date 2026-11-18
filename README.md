# Salary Estimate Classification

An educational machine learning project classifying job-posting salary estimates as below or at/above the median of the training salaries. This is a relative salary category, not a measure of employee satisfaction or actual pay.

## Files

- `salary_analysis.ipynb`: data cleaning, model comparison, and evaluation.
- `df.csv`: input data, required alongside the notebook but not necessarily distributed in this repository.
- `requirements.txt`: dependencies for the tested environment.

## Run

Use Python 3, obtain the input file separately if it is not included, and put `df.csv` in the same directory as the notebook. From that directory, run:

```bash
pip install -r requirements.txt
jupyter notebook
```

Open `salary_analysis.ipynb` and run all cells in order.

## Method and results

The notebook cleans annual salary ranges, removes exact duplicate postings, and uses the range midpoint as an approximate salary in thousands of dollars. A 30% test set is reserved before the target threshold is calculated from training salaries. Preprocessing is fitted inside each cross-validation fold. Logistic regression, K-nearest neighbors, a decision tree and a random forest are compared with a majority-class baseline. Selection uses training cross-validation accuracy.

In the recorded run, the training median was $101.5K. Random forest was selected with approximately 70.0% mean cross-validation accuracy; test accuracy was 69.8% on 1,458 postings. These figures depend on the split and should not be treated as guaranteed future performance. The target threshold used in cross-validation is fixed from the complete training partition.

## Limitations

- Salary ranges are estimates, not verified compensation, and the target does not measure satisfaction.
- Removing hourly or missing entries and applying location and salary filters can introduce selection bias.
- Random splitting may put related postings from the same employer in training and test sets. Results do not establish performance for new employers or future periods.
- This is an educational analysis, not a basis for compensation decisions.

## Data source

The provenance, collection period and redistribution license of the supplied `df.csv` have not been verified. Confirm the source, publication rights and whether the data contains personal information before publishing it.
