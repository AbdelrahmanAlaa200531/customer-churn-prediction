# Customer Churn Analysis and Prediction

A Jupyter Notebook project for exploring customer churn data, comparing classification models, and building a simple churn prediction interface. The notebook includes exploratory data analysis, feature encoding, model evaluation, and pickle-based model saving.

## Project overview

The notebook follows this workflow:

1. Loads the provided customer churn training and testing CSV files and combines them into one dataset.
2. Cleans the data by removing a row with missing values and dropping the customer ID field.
3. Explores numeric and categorical features with charts and summary statistics.
4. Examines churn patterns across customer attributes and reviews numeric correlations.
5. Splits the combined dataset into training and test subsets.
6. One-hot encodes categorical features and compares several classifiers with stratified 5-fold cross-validation.
7. Evaluates Decision Tree, Random Forest, and XGBoost models.
8. Saves a fitted Random Forest model and categorical encoder, then provides a `CustomerChurnClassifier` example for single-customer predictions.

## Files

```text
.
├── Customer_Churn.ipynb
├── customer_churn_dataset-training-master.csv
└── customer_churn_dataset-testing-master.csv
```

The CSV files are expected by the notebook but are not included here. Make sure you have permission to use and redistribute the data before adding it to a public repository. Otherwise, provide a link and attribution to the dataset source.

## Run in Google Colab

1. Upload `Customer_Churn.ipynb` to [Google Colab](https://colab.research.google.com/).
2. Upload both CSV files to the Colab session. The notebook expects them under `/content` with these exact names:
   - `customer_churn_dataset-testing-master.csv`
   - `customer_churn_dataset-training-master.csv`
3. Select **Runtime → Run all**.
4. At the end, the notebook creates `encoder.pkl` and `customer_churn_random_forest_model.pkl` in the current session.
5. Download those files from the Colab Files panel if you want to keep them after the session ends.

## Run locally

The notebook reads the CSVs from `/content`, which is a Colab path. To run locally, update the two `pd.read_csv(...)` paths near the top of the notebook to point to the CSV files on your computer.

Install the commonly used dependencies in a Python environment:

```bash
pip install numpy pandas seaborn matplotlib scikit-learn xgboost notebook
```

Then start Jupyter, open `Customer_Churn.ipynb`, and run all cells:

```bash
jupyter notebook
```

## Models and notebook metrics

The notebook reports the following mean cross-validation metrics from its saved run:

| Model | Accuracy | Precision | Recall |
|---|---:|---:|---:|
| Logistic Regression | 0.84 | 0.87 | 0.85 |
| Gaussian Naive Bayes | 0.86 | 0.91 | 0.83 |
| Multinomial Naive Bayes | 0.74 | 0.81 | 0.70 |
| K-Nearest Neighbors | 0.84 | 0.89 | 0.83 |
| Decision Tree | 0.88 | 0.90 | 0.88 |
| Random Forest | 0.93 | 0.90 | 1.00 |
| XGBoost | 0.93 | 0.90 | 0.99 |

In the saved holdout evaluation, the Random Forest reports 0.93 accuracy, 0.90 precision, and 1.00 recall. These are the notebook's recorded results and may vary with data files and library versions. They should be interpreted in light of the data-splitting limitation below.

## Making a prediction

The notebook defines a `CustomerChurnClassifier` wrapper and demonstrates a prediction using values for age, tenure, usage frequency, support calls, payment delay, total spend, last interaction, gender, subscription type, and contract length. It returns either `Will Churn` or `Won't Churn`.

The notebook saves these artifacts:

- `customer_churn_random_forest_model.pkl`
- `encoder.pkl`

Keep both files together when using the wrapper. The code uses Python pickle; only load pickle files from trusted sources.

## Important evaluation note

The notebook combines the files named `testing` and `training` first, then makes a new random train-test split. As a result, its reported holdout metrics are **not an evaluation on the original untouched test file**. For a more reliable estimate, keep the supplied test file separate, train and tune using only the training file, and evaluate on the original test data once at the end. The notebook's metrics are useful as exploratory results, not as a final guarantee of performance in production.

Other limitations include using a fixed 0.5 decision threshold and not reporting probability calibration or a business cost analysis for missed churn versus unnecessary retention offers.

## License and attribution

Add a software license for this project and cite the original dataset source and its terms of use before publishing. This repository does not claim ownership of third-party data.
