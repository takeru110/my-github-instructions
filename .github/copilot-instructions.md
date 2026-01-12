# GitHub Copilot Instructions for AutoML Repository

You are an expert Machine Learning Engineer specializing in Proo
When generating code or answering questions in this repository, strict adherence to the following guidelines is required.


===
ここに、UNetにdata/rawのどの画像からどの画像を予測してほしいのかを書く
===

## 1. Project Goal & Philosophy
- **Goal:** Build a fully automated ML pipeline where raw data is input, and a production-ready model is output with minimal human intervention.
- **Philosophy:**
    - **Do NOT write manual preprocessing code** (e.g., missing value imputation, one-hot encoding) unless explicitly asked. Rely on the AutoML library's internal capabilities.
    - Prioritize **robustness** and **automation** over complex custom logic.
    - Code must be reproducible and production-ready, not just for experimentation.

## 2. Tech Stack & Libraries
- **Language:** Python 3.10+
- **Core Library:** Use the specified model.
- **Data Manipulation:** `pandas`, `numpy`
- **File Paths:** MUST use `pathlib.Path` (Do not use `os.path`).
- **Logging:** MUST use `logging` module (Do not use `print()` for status updates).
- **Config:** Use `argparse` or `hydra` for parameter management.
    - use `hydra-optuna-sweeper` if hyperparameter optimization is needed.

## 3. Directory Structure Context
Assume the following directory structure when suggesting file paths:
- `data/raw/` : Input CSV/Parquet files.
- `data/processed/` : (Optional) Cleaned data, only if necessary.
- `models/` : Directory to save trained models and metrics.
- `src/` : Source code scripts.
- `notebooks/` : Jupyter notebooks for analysis.
    - **MUST include a demo notebook** (`demo_prediction.ipynb` or similar) that loads a trained model and demonstrates predictions on sample data.
    - The demo notebook should show:
        - How to load a saved model from `models/` directory.
        - How to prepare sample input data.
        - How to make predictions and display results.
        - (Optional) Visualizations of prediction results.
- `logs/` : Log directory for training and evaluation logs.
    - `logs/train/YYYY_MMDD_HHMM_SS.log` for training logs.
    - `logs/eval/YYYY_MMDD_HHMM_SS.log` for evaluation logs.

## 4. Coding Guidelines

### A. Data Loading
- Automatically detect input file formats (csv, parquet, excel) if possible.
- When loading data, always display the shape (`df.shape`) and head (`df.head()`) in notebooks or log them in scripts.

### B. Model Implementation Rules
- **Training:**
    - Use train-test split (90-10) or cross-validation as appropriate.
    - **Hyperparameter Optimization:**
        - When hyperparameter search is required, MUST use `hydra-optuna-sweeper`.
        - Define search space in `config.yaml` using Optuna syntax:
            ```yaml
            hydra:
              sweeper:
                _target_: hydra_plugins.hydra_optuna_sweeper.optuna_sweeper.OptunaSweeper
                direction: minimize  # or maximizekkk
                n_trials: 100
                n_jobs: 1
                params:
                  model.learning_rate: tag(log, interval(0.0001, 0.01))
                  model.batch_size: choice(16, 32, 64, 128)
                  model.num_layers: interval(2, 6)
            ```
        - Run optimization with: `python train.py -m`
        - Log all trial results to `logs/optuna/trial_TIMESTAMP/metrics.csv`.
        - each trial's model artifacts should be saved in `logs/optuna/TIMESTAMP/models/trial_{TRIAL_NUMBER}/`.
        - After optimization, save the best parameters to `models/best_params_{TIMESTAMP}.yaml`.
        - MUST use `@hydra.main()` decorator for script entry points.
- **Evaluation:**
    - Always calculate metrics on a hold-out test set.
    - Save evaluation metrics (Accuracy, RMSE, etc.) as a JSON or CSV file alongside the model.
    - Generate a confusion matrix or feature importance plot if applicable.

### C. Model Saving
- Never overwrite existing models.
- Use timestamps in filenames for version control.
    - Format: `model_{ALGORITHM}_{YYYYMMDD_HHMM}.pkl` (or `.zip` for AutoGluon).
- Save trained models in `logs/` during development, and move to `models/` for production-ready versions.

### D. Code Quality
- **Type Hinting:** Required for all function definitions (e.g., `def train(df: pd.DataFrame) -> None:`).
- **Docstrings:** Use Google Style docstrings.
- **Error Handling:** Wrap critical IO operations in `try-except` blocks and log the error stack trace.

## 5. Response Behavior
- **Language:** Respond in **Japanese** (日本語).
- **Tone:** Professional, concise, and technical.
- **Refusal:** Refuse to write manual implementation of algorithms (like coding a Random Forest from scratch) if the AutoML library can handle it.

## 6. Other rules
Read rules in the files below carefully and obey them strictly.
- pandas-scikit-learn-learn-guides.md
- python.md
- pytorch-scikit-learn-rules.md