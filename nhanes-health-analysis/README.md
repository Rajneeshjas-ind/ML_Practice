# Diabetes, BMI & Cholesterol in NHANES

Exploratory health-data analysis in Python on the NHANES survey: data-quality audit, EDA, simulation, and subgroup comparisons.

## Questions
1. How do **BMI** and **total cholesterol** differ between adults who report diabetes and those who don't?
2. How do **diabetes prevalence** and **cholesterol** differ between current/former smokers and never smokers?

## Key findings (adults aged 20+)
| Comparison | Group A | Group B |
|---|---|---|
| Mean BMI: diabetes vs no diabetes | **31.9** kg/m² | 28.3 kg/m² |
| Share with BMI > 30: diabetes vs no diabetes | **55.5%** | 32.9% |
| Mean total cholesterol: diabetes vs no diabetes | 4.81 mmol/L | **5.08** mmol/L |
| Reported diabetes: current/former smokers vs never smokers | **13.0%** | 10.3% |
| Mean total cholesterol: current/former smokers vs never smokers | 5.05 mmol/L | 5.05 mmol/L |

The diabetes group carries noticeably more weight but *lower* average cholesterol. Smoking history tracks with diabetes prevalence but not with cholesterol. All of these are unadjusted associations: age and other factors aren't controlled for.

## What's in the analysis
- **Missing-data audit using survey rules.** I split *structural* missingness (age-ineligible respondents, skipped questions) from genuinely missing answers, based on CDC/NHANES eligibility documentation, instead of dropping or filling blindly.
- **Data cleaning.** Recoded the 80+ age cap, removed repeated records (10,000 → 6,721 rows), and checked outliers with both IQR and ±3 SD rules. Each outlier decision is justified case by case: short heights kept because they belong to toddlers, extreme weights excluded.
- **EDA.** Distributions, scatterplots and contingency tables across age, pulse, height, weight, income, education, smoking and housing.
- **Simulation.** 10,000 bootstrap samples of systolic blood pressure demonstrate the central limit theorem (simulated SE 2.48 vs theoretical 2.49 mmHg). Binomial simulations cross-check the subgroup diabetes rates.
- **Subgroup comparisons.** Group summaries, boxplots, percentage bar charts and empirical CDFs.

## Data
`data/nhanes.csv` is an NHANES extract with 10,000 records and 76 variables (demographics, body measures, lab results, lifestyle). NHANES is run by the U.S. CDC's National Center for Health Statistics.

## Run it
```bash
pip install pandas numpy matplotlib seaborn scipy
jupyter notebook nhanes_analysis.ipynb
```

## Tools
Python · pandas · NumPy · Matplotlib · Seaborn · SciPy · Jupyter

## Limitations
These are associations, not causes. Results aren't age-adjusted or survey-weighted, and the extract is resampled. Removing duplicates and excluding high weights changes the sample composition.
