# Copilot instructions 

## Goal
- Build an automated pipeline: raw data -> production-ready model
- This repository is in a PoC/experimental phase: prefer clarity and fast iteration over heavy abstraction.
- Avoid overusing try/except and complex branching; handle only I/O and external-boundary failures explicitly.


## Philosophy
- Prefer popular libraries over manual preprocessing.
- Keep changes minimal; avoid unrelated refactors.
- Code must be reproducible and production-ready.

## Tech constraints
- Python 3.10+
- Use pathlib.Path (no os.path)
- Use logging (no print)
- configuration parameter management: hydra or argparse (prefer hydra for training scripts)

## Project structure 
- `README.md` : Project overview and instructions.
- `docs/internal/`: Internal specifications and design notes.
- `data/raw/`: Raw input datasets like CSV.
- `data/processed/`: Optional intermediate datasets (only when necessary).
- `models/`: Versioned trained models and metrics for reuse.
- `src/`: Library and CLI scripts (training/evaluation/inference).
- `notebooks/`: Analysis, demo, and data analysis notebooks.
- `notebooks/<model_name>/`: Model-specific notebooks (e.g., demo_prediction.ipynb).
- `notebooks/data_analysis/`: Data analysis notebooks.
- `logs/`: Experiment logs (train/eval) and run metadata.

### Model-scoped code and logs (required)
- Organize code and run artifacts by model name so experiments are easy to identify.
- Do not place top-level entry points like `src/train.py`, `src/unet/train.py` or `src/eval.py` directly under `src/`.
- Use the following layout for each model (example: `unet`):
  - Code: `src/<model_name>/{train,eval,infer}/...` (e.g., `src/unet/train/`)
  - Logs: `logs/<model_name>/{train,eval,infer}/...` (e.g., `logs/unet/train/`)

## Response behavior
- Respond in Japanese.
- Do not implement algorithms from scratch if a well-used library function exists.