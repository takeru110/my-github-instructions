---
applyTo: "src/**/*.py"
---

# Logging instructions

## General
- Use the `logging` module (do not use `print()` for status updates).
- Do not log secrets, tokens, credentials, or private URLs.
- Prefer structured, actionable logs: include key parameters and dataset/model identifiers when relevant.

## Log directory layout
- Store logs under `logs/` at the repository root.
- Use these subdirectories:
  - `logs/<model_name>train/` for training runs
  - `logs/<model_name>/eval/` for evaluation runs
  - `logs/<model_name>/infer/` for inference/prediction runs (if applicable)
  - `logs/<model_name>/optuna/` for hyperparameter optimization runs (if applicable)

## File naming
- Never overwrite existing log files.
- Use timestamps in filenames: `{YYYYMMDD_HHMMSS}` (local time).
- Recommended filenames:
  - `logs/<model_name>/train/train_{YYYYMMDD_HHMMSS}.log`
  - `logs/<model_name>/eval/eval_{YYYYMMDD_HHMMSS}.log`
  - `logs/<model_name>/infer/infer_{YYYYMMDD_HHMMSS}.log`
  - `logs/<model_name>/optuna/optuna_{YYYYMMDD_HHMMSS}.log`

## Logger configuration
- Configure logging in a reusable helper (e.g., `src/<model_name>/utils/logging_utils.py`) and import it.
- Always log to both:
  - a file under `logs/...`
  - stdout (console)
- Use log levels appropriately:
  - `DEBUG` for detailed diagnostics
  - `INFO` for run progress and key milestones
  - `WARNING` for recoverable issues
  - `ERROR` for failures (include exception stack trace)
- Format should include at least: timestamp, level, logger name, message.
  - Example format: `%(asctime)s %(levelname)s %(name)s %(filename)s:%(lineno)d %(funcName)s - %(message)s`


## What to log (minimum)
- Start-of-run metadata:
  - command-line/config parameters (excluding secrets)
  - data path(s) and basic dataset summary (e.g., shape, split sizes)
  - model name/version and important hyperparameters
- Milestones:
  - training start/end, epoch or step progress (if applicable)
  - evaluation start/end and key metrics
  - artifact save paths (models/metrics)
- Errors:
  - wrap IO-heavy operations in try/except and log stack traces with `logger.exception(...)`

## Hydra / multi-run (if used)
- If using Hydra multi-run (e.g., Optuna sweeper), include trial/run identifiers in logs.
- Prefer writing per-run log files so parallel runs do not collide.
