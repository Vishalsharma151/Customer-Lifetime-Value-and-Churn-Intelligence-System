# Notebook 03 — Feature Engineering and Model Preparation

## Project: Customer Lifetime Value and Churn Intelligence System (CHURNIQ)

### Overview
This notebook prepares the engineered customer data for machine learning by separating the features and target variable into training and testing datasets. It then saves these datasets as CSV files for reuse in subsequent modeling notebooks.

### Objectives
- Prepare training and testing feature matrices.
- Separate the target variable, `churn_target`, from the input features.
- Save the datasets in the project's `models` directory.
- Create reusable files for training and evaluating churn prediction models.

### Files Generated

The following files are saved in the `models` directory:

| File | Description |
|---|---|
| `X_train.csv` | Features used to train the model |
| `X_test.csv` | Features used to evaluate the model |
| `y_train.csv` | Target labels for training |
| `y_test.csv` | Target labels for testing |

### Code Summary

The notebook uses Python's `pathlib` module to create the output directory and Pandas to export the datasets.

```python
from pathlib import Path

output_dir = Path("../models")
output_dir.mkdir(parents=True, exist_ok=True)

X_train.to_csv(output_dir / "X_train.csv", index=False)
X_test.to_csv(output_dir / "X_test.csv", index=False)

y_train.to_csv(
    output_dir / "y_train.csv",
    index=False,
    header=["churn_target"]
)

y_test.to_csv(
    output_dir / "y_test.csv",
    index=False,
    header=["churn_target"]
)
```

### Expected Output

After successful execution, the notebook displays:

- Confirmation that the datasets were saved.
- The shapes of `X_train`, `X_test`, `y_train`, and `y_test`.
- The absolute path of the output directory.

The exact row and column counts depend on the dataset and the train-test split.

### Project Structure

```text
CHURNIQ/
├── models/
│   ├── X_train.csv
│   ├── X_test.csv
│   ├── y_train.csv
│   └── y_test.csv
├── notebooks/
│   └── 03_Feature_Engineering_and_Model_Preparation.ipynb
└── README.md
```

*Note: The structure above is illustrative. The relative path `../models` saves files one directory above the notebook's current working directory.*

### Next Steps

The saved datasets can be loaded into the next notebook to:

1. Train a Logistic Regression model.
2. Train a Random Forest classifier.
3. Evaluate model performance using precision, recall, F1-score, and ROC-AUC.
4. Identify customers who are likely to churn.

### Technologies Used
- Python
- Pandas
- pathlib
- Jupyter Notebook
- Scikit-learn (for subsequent modeling)

### Author
Vishal Sharma

GitHub: [@vishalsharma151](https://github.com/vishalsharma151)
