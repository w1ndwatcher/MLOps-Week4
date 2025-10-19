# IRIS Homework Pipeline - MLOps Assignment

This repository contains the implementation of an IRIS dataset pipeline with DVC-based data versioning, CI/CD integration using GitHub Actions, unit tests, and model evaluation.

---

## **Directory Structure**
```
├── data/
│ └── iris.csv
├── model/
│ └── model.joblib
├── train.py
├── tests/
│ ├── test_data_validation.py
│ └── test_model_eval.py
└── requirements.txt
```

---

## **File Descriptions**

### **data/iris.csv**
- The IRIS dataset used for training and evaluation.
- Tracked using DVC to enable reproducible experiments.
- Contains features: `sepal_length`, `sepal_width`, `petal_length`, `petal_width` and target column `species`.

### **model/model.joblib**
- The trained IRIS classification model.
- Saved in Joblib format.
- Tracked using DVC to ensure versioned model artifacts.

### **train.py**
- Python script to train the IRIS classification model using `scikit-learn`.
- Steps include:
  1. Loading dataset from `data/iris.csv`.
  2. Splitting data into training and test sets.
  3. Training a classifier.
  4. Saving the trained model to `model/model.joblib`.
- Output: `model.joblib` stored in `model/`.

### **tests/test_data_validation.py**
- Contains unit tests to validate the input dataset.
- Checks include:
  - No missing values in the dataset.
  - Correct column names.
  - Correct data types.
  - Unique values in the `species` column.
- Run using `pytest` to ensure data integrity before training or evaluation.

### **tests/test_model_eval.py**
- Contains unit tests to evaluate the trained model.
- Checks include:
  - Model predictions have correct shape.
  - Model achieves acceptable accuracy on the test set (above 90%).
- Ensures reproducibility and correct performance of the trained model.

### **requirements.txt**
- Contains all Python dependencies required to run the pipeline, including:
  - `pandas`, `numpy`, `scikit-learn` for data processing and model training.
  - `pytest` for testing.
  - `dvc` and `dvc-gs` for data and model versioning with Google Cloud Storage (GCS).

---

## **Usage Instructions**

1. Clone the repository:

```bash
git clone [https://github.com/yourusername/IRIS-MLOps-Pipeline.git](https://github.com/w1ndwatcher/MLOps-Week4.git)
cd MLOps-Week4

pip install -r requirements.txt

dvc pull

python train.py
```

Push the changes or create a pull request and the workflow will automatically test and evaluate the model.

