---
applyTo: "src/**/*.py"
---

# Python quality rules

## Runtime / dependencies

- Default to the approved libraries are numpy, pandas, pyarrow, scikit-learn, torch, torchvision, Pillow, matplotlib, seaborn, hydra-core, omegaconf, optuna, hydra-optuna-sweeper, tqdm, joblib, opencv-python, scipy, statsmodels.
- If another library is clearly a better fit, you may use it.

## Paths / I-O
- Use `pathlib.Path` for all file paths (no `os.path`).
- Wrap critical I/O in try/except and log stack traces via `logger.exception(...)`.

## Logging / security
- Use the `logging` module for status updates (no `print()`).
- Never log secrets, tokens, credentials, or private/internal URLs.

## Code quality
- Type hints are required for all functions and methods.
- Use Google-style docstrings for public APIs and non-trivial functions/classes.
- Follow PEP 8 naming conventions and keep functions small and focused.

## Data/code performance (when applicable)
- Prefer vectorized operations (`pandas`/`numpy`) over explicit Python loops.
- Use explicit indexing with `loc`/`iloc`; use `groupby` for aggregations when appropriate.
