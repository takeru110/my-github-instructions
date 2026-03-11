---
name: plot
description: A Jupyter Notebook template for drawing line plots with Japanese labels using matplotlib and seaborn. This template is used by Copilot when creating line plots.
license: MIT
---

A Jupyter Notebook template for drawing line plots with Japanese label support using matplotlib and seaborn. Used by Copilot when creating line plots.
	
# SKILL: Line Plot ipynb Template

## Overview
This is a Notebook template for line plots using matplotlib, seaborn, and numpy. It explicitly sets the font to prevent garbled Japanese labels and titles.

## Template Code

```python
# Japanese font setting (to prevent garbled text)
import matplotlib
matplotlib.rcParams['font.family'] = 'IPAexGothic'  # If not available, use 'Noto Sans CJK JP' or similar

import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_style("darkgrid")

# Generate dummy data
n_points = 50
x = np.linspace(0, 10, n_points)
y = np.sin(x) + np.random.normal(0, 0.1, n_points)

fig, ax = plt.subplots(figsize=(8, 5))
ax.plot(x, y, linestyle='-', linewidth=2, color='tab:blue', label='Sample')
ax.set_xlabel('Time (s)', fontsize=14)
ax.set_ylabel('Value', fontsize=14)
ax.set_title('Line Plot Sample', fontsize=16, fontweight='bold')
ax.grid(True, color='white', linewidth=1.2, alpha=0.7, linestyle='--')
plt.legend(loc='upper left', fontsize=12, frameon=True, edgecolor='white', facecolor='white', framealpha=0.8)
plt.tight_layout()
plt.show()
```

## Key Points
- Explicitly set fonts to prevent garbled Japanese labels and titles.
- Uses matplotlib, seaborn, and numpy.
- Axis labels, titles, and legends can be written in Japanese.
- Style settings focused on graph readability.
- Use this template as a reference; prefer larger fonts and thicker lines.
- Keep figures small (e.g., `figsize=(8, 5)` or smaller).


## Usage
Paste this template at the beginning of your Notebook and edit the data and labels as needed.
