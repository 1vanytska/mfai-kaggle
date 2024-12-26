# Exploring Mental Health Data

This project explores the application of machine learning concepts to mental health data. The goal is to predict whether an individual is experiencing depression based on survey data, leveraging preprocessing techniques, feature engineering, and model optimization.

---

# Useful Links
## [PM Tool](https://github.com/1vanytska/mfai-kaggle/issues)
## [File Storage](https://drive.google.com/drive/folders/1P6gKHTLOxxjnGIclBhXBG1tJppyYzlhc?usp=drive_link)
## [Kaggle](https://www.kaggle.com/competitions/playground-series-s4e11/overview)

---

## Getting Started

### 1. Understanding the Task

#### 1.1 What are we trying to predict (target variable)?

We aim to predict whether a person is suffering from depression (target column: `Depression`). This is a binary classification problem where:

- `0`: No depression
- `1`: Depression present

#### 1.2 What are the evaluation metrics?

The primary evaluation metric for this task is **accuracy**, which measures the percentage of correct predictions out of the total examples in the test dataset.

#### 1.3 Input and Output Data Format

**Input Data:**

- A dataset with columns including:
  - `id`: Unique identifier for each record.
  - Demographic data: e.g., `age`, `gender`, `city`.
  - Work/education-related attributes: e.g., `CGPA`, `Work Pressure`, `Academic Pressure`.
  - Other personal data: e.g., `Sleep Duration`, `Dietary Habits`.
- *Note: The dataset contains missing values that require handling.*

**Output Data:**

- A file `submission.csv` with two columns:
  - `id`: Unique identifier from the test dataset.
  - `Depression`: Predicted binary value (0 or 1).

Example:

```
id,Depression
140700,0
140701,0
140702,1
```

---

## Implementation Steps

### 2. Data Preprocessing

#### 2.1 Handling Missing Values

- Combined the `Academic Pressure` and `Work Pressure` columns into a unified `Pressure` column.
- Combined the `Study Satisfaction` and `Job Satisfaction` columns into a unified `Satisfaction` column.
- Used median values to fill missing entries in `Pressure`, `Satisfaction`, and `Financial Stress`, with separate handling for student and professional groups.

#### 2.2 Feature Selection

Dropped irrelevant or redundant columns:

- `CGPA`, `Name`, `City`, `Profession`, `Academic Pressure`, `Work Pressure`, `Study Satisfaction`, `Job Satisfaction`, `Degree`, `Family History of Mental Illness`, `Gender`, `Have you ever had suicidal thoughts?`, `Sleep Duration`, and `Dietary Habits`.

### 3. Feature Transformation

- Used a preprocessing pipeline:
  - **Imputation:** Filled missing values with the mean.
  - **Scaling:** Standardized features using `StandardScaler`.

---

### 4. Model Training and Evaluation

#### 4.1 Random Forest Classifier with Hyperparameter Tuning

- Used `RandomizedSearchCV` for hyperparameter tuning with a parameter grid:
  - Number of estimators (`n_estimators`): [50, 100, 200]
  - Maximum depth (`max_depth`): [10, 20, 30, None]
  - Minimum samples split (`min_samples_split`): [2, 5, 10]
  - Minimum samples leaf (`min_samples_leaf`): [1, 2, 4]
  - Maximum features (`max_features`): ['sqrt', 'log2']
- Trained the model using 5-fold cross-validation.
- Selected the best model based on accuracy.

#### 4.2 Logistic Regression with GridSearchCV

- Hyperparameter tuning with:
  - Regularization strength (`C`): [0.001, 0.01, 0.1, 1, 10, 100]
  - Solver (`solver`): ['liblinear', 'lbfgs', 'saga']
  - Maximum iterations (`max_iter`): [100, 200, 300, 500]
- Evaluated feature importance using logistic regression coefficients.

#### 4.3 Model Evaluation

- Calculated accuracy for both training and validation datasets to assess model performance.
- Printed feature importance to understand key predictors.

---

### 5. Test Data Preparation

- Applied the same preprocessing transformations to the test data as used for the training and validation data.
- Generated predictions using the best model.

---

### 6. Submission

- Created a submission file with two columns:
  - `id`: Unique identifier.
  - `Depression`: Predicted values.
- Saved the predictions to `submission.csv` for final evaluation.

---

## Key Scripts

### Preprocessing

- Imputation of missing values for key columns (`Pressure`, `Satisfaction`, `Financial Stress`).
- Feature transformation with scaling and removal of unnecessary columns.

### Model Training

- Random Forest Classifier and Logistic Regression, both optimized using hyperparameter tuning.
- Validation and selection of the best-performing model.

### Prediction and Submission

- Generating predictions on the test dataset.
- Formatting and saving the predictions in the required format.

---

## Results

- **Random Forest Accuracy:** Achieved `~0.92` on validation data.
- **Logistic Regression Accuracy:** Similar performance with feature importance analysis for interpretability.

---

## Future Work

- Explore other models like Gradient Boosting or Neural Networks.
- Fine-tune hyperparameters further for improved performance.
- Conduct feature engineering to derive additional meaningful features.

---

## Dependencies

- Python 3.x
- Libraries: `pandas`, `numpy`, `sklearn` (scikit-learn)

---

## Running the Code

1. Clone the repository.
2. Ensure all dependencies are installed.
3. Place the input dataset files (`train.csv` and `test.csv`) in the working directory.
4. Run the script to generate the submission file.

