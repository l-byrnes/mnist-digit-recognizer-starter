# MNIST Digit Recognizer — five-stage machine learning project

A sequence of five self-contained Jupyter notebooks for the [Kaggle Digit Recognizer competition](https://www.kaggle.com/competitions/digit-recognizer). The first four stages use scikit-learn; the final stage uses **TensorFlow/Keras** for a convolutional neural network.

## Setup (Python 3.14, macOS / VS Code)

1. Open this folder in VS Code.
2. Create a virtual environment: `python3.14 -m venv .venv` (or use the VS Code **Python: Create Environment** command).
3. Activate it: `source .venv/bin/activate` (Windows: `.venv\Scripts\activate`).
4. Install: `python -m pip install --upgrade pip` then `python -m pip install -r requirements.txt`.
5. In VS Code, select the `.venv` kernel for each notebook.
6. Download `train.csv` and `test.csv` from Kaggle's **Data** tab and put both files inside `data/`.
7. Open `notebooks/01_knn.ipynb` and run all cells.

**Compatibility note:** The requirements file pins the TensorFlow 2.22 release candidate for Python 3.14. This is prerelease software. If pip cannot find a matching wheel for your OS/CPU, run `python -m pip index versions tensorflow --pre` to check available versions, and use a compatible TensorFlow build. Do not install an unrelated Python version without checking the error first.

## Notebooks

| Notebook | Model | Key idea |
| --- | --- | --- |
| `01_knn.ipynb` | K-nearest neighbors | Distance and baseline accuracy |
| `02_random_forest.ipynb` | Random forest | Ensembles of decision trees |
| `03_svc.ipynb` | RBF support vector classifier | Kernel-based classification |
| `04_mlp_sklearn.ipynb` | Scikit-learn MLP | Dense neural networks |
| `05_tensorflow_cnn.ipynb` | TensorFlow/Keras CNN | Convolution and spatial structure |

Each notebook loads Kaggle data independently, creates the **same stratified 80/20 holdout** (`random_state=42`), evaluates performance, displays misclassified digits, and generates a submission CSV under `submissions/`.

## Kaggle format

- `train.csv`: 42,000 rows, a `label` column and 784 pixel columns.
- `test.csv`: 28,000 rows with 784 pixel columns and no labels.
- Submission: `ImageId,Label`, one row per test image, with ImageId starting at 1.

**Important:** Do not use the Kaggle `test.csv` as a validation set. Compare models using the notebook holdout, then retrain on all labeled rows before generating Kaggle predictions.

## Student questions

1. Which model has the highest validation accuracy? Which trains fastest?
2. What digits are most frequently confused?
3. Does increasing model complexity always improve validation accuracy?
4. How does the CNN exploit the image's spatial structure?
5. How does Kaggle leaderboard accuracy compare with local validation accuracy?

## Folder structure

```text
mnist-digit-recognizer/
├── README.md
├── requirements.txt
├── .gitignore
├── data/                  # download Kaggle CSV files here
├── notebooks/
│   ├── 01_knn.ipynb
│   ├── 02_random_forest.ipynb
│   ├── 03_svc.ipynb
│   ├── 04_mlp_sklearn.ipynb
│   └── 05_tensorflow_cnn.ipynb
└── submissions/           # generated automatically
```
