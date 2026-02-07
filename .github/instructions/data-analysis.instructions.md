---
applyTo: "notebooks/**/data_analysis/**/*.ipynb"
---

# Data Analysis Notebook Instructions

## Scope
- Use EDA notebooks for exploration, hypothesis checks, and communicating findings.
- Do not implement production logic in notebooks; move reusable code to `src/` and import it.

## Tech
- Python 3.10+.
- Data: use `pandas` (+ `numpy` when needed).
- Paths: use `pathlib.Path` (no `os.path`).
- Plotting: use `matplotlib` by default; use `seaborn` only when the same plot would be significantly harder or less readable with matplotlib alone.
- Do not introduce new third-party dependencies unless explicitly requested.

## Reproducibility
- The notebook must run top-to-bottom with "Run All" without manual intervention.
- Put all imports and global constants near the top.
- If randomness is used, set and document a fixed seed near the top.
- Avoid hidden state across cells; make dependencies explicit.
- Record the input data location and key assumptions in markdown.

## Required notebook structure
- First cell (markdown) must include: purpose, input data location, and expected outputs.
- Use clear section headings (markdown), e.g.:
  - Data loading
  - Data overview
  - Data quality checks
  - Univariate analysis
  - Bivariate analysis / relationships
  - Target analysis (if applicable)
  - Findings and next steps
- Each section should start with a short markdown plan (what you will check and why).

## Minimum EDA checklist
- After loading data, show a small, reviewable summary:
  - dataset shape, column list, dtypes, and a small preview (`head()` / `sample()`).
- Data quality checks (at minimum):
  - missing values, duplicates, dtype issues, obvious out-of-range values.
- Missing-data policy must be explicit:
  - choose imputation, removal, or flagging (and state which one you use and why).
- If a target/label exists:
  - define the target clearly, check class balance (classification) or distribution (regression),
  - look for obvious leakage signals.
- If a time axis exists:
  - check time ordering, time-based leakage risks, and distribution drift.

## Outputs and performance hygiene
- Keep cell outputs small; avoid printing large tables.
- Prefer summaries (`describe()`, value counts, small samples) over full dumps.
- Save large intermediate outputs/figures to disk when needed to keep notebooks lightweight.

## Plotting rules
- All plots must have English axis labels (and units when applicable).
- Include a legend when multiple series are shown.
- Prefer one figure per cell.
- Add a short markdown takeaway under each figure/table (what it shows and why it matters).


## Language
- Use Japanese for all Markdown explanations.
