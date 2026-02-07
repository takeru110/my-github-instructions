---
applyTo: "notebooks/**/*.ipynb"
---

# Notebook instructions

- Notebooks are for EDA and demos; keep production logic in `src/`.
- Must be reproducible: "Run All" top-to-bottom with no manual steps; set a fixed seed if randomness is used.
- Put imports and global constants at the top; avoid hidden state between cells.

## Tech
- Python 3.10+; use `pandas` (+ `numpy` if needed).
- Paths: `pathlib.Path` only (no `os.path`).
- Plotting: `matplotlib` by default; use `seaborn` only when the same plot would be significantly harder or less readable with matplotlib alone.

## Notebook structure
- First cell: markdown with purpose, input data location, expected outputs.
- Use section headings; keep cells- Each section must start with a markdown cell explaining the plan and assumptions.
- For non-trivial code cells, add a short markdown cell before the code explaining intent and expected output. focused and add brief comments where helpful.
- Keep outputs small (`head()` / `sample()` / `describe()`); do not print large tables.
- Never print/log secrets, tokens, credentials, or private URLs.

## Plots
- English axis labels (and units when applicable); add legend when needed.
- Prefer one figure per cell; avoid hard-coded colors unless explicitly requested.
- Add a brief markdown takeaway under each figure/table.
- Encapsulate plotting into reusable functions to keep figure formatting consistent (labels, legends, etc.).

## Demo notebook (when inference changes)
- If you propose/modify prediction or inference code, provide/update `notebooks/<model_name>/demo_prediction.ipynb` that loads a model from `models/<model_name>/`, prepares sample input, runs predictions, and visualizes results when meaningful. Keep it fast.

## Data analysis notebooks (when applicable)

- Always start analysis with data exploration and summary statistics (e.g., shape, describe).
- Run data quality checks at the beginning (missing values, dtypes, value ranges, duplicates, etc.).
- Make the missing-data policy explicit and handle it via imputation, removal, or flagging.

## Language
- Use Japanese for all explanations.
- Use English for comments and texts in plots.