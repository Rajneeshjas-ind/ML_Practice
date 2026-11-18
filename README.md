# ML_Practice

Python, data analysis and machine learning work.

## Contents

| Folder | What's inside |
|---|---|
| `nhanes-health-analysis/` | Exploratory health analysis of NHANES survey data: diabetes, BMI, cholesterol and smoking history (dataset in `data/`) |
| `learning/` | Python, probability and ML practice notebooks, and `CarDekho-EDA/`: exploratory analysis of used-car listings (dataset in `data/raw/`) |
| `learning/regression-regularization/` | OLS vs Ridge vs Lasso practice on the Hitters baseball salary data |

## Running the notebooks

Clone the repo, open a notebook in VS Code or Jupyter, and run it from its own folder. Every project keeps its data in its own `data/` folder and loads it with a relative path:

- `nhanes-health-analysis/` → `data/nhanes.csv`
- `learning/CarDekho-EDA/` → `data/raw/Car details v3.csv`
- `learning/regression-regularization/` → `data/hitters.csv`
