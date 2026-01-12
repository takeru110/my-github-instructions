---
description: Guidance on initial data exploration steps within data analysis scripts, including summary statistics and data validation.
globs: **/data_analysis/*.py
---
- Begin analysis with data exploration and summary statistics.
- Implement data quality checks at the beginning of analysis.
- Handle missing data appropriately (imputation, removal, or flagging).---
description: Defines rules for creating informative and visually appealing plots using matplotlib and seaborn, emphasizing proper labels, titles, legends, and color schemes.
globs: **/*.py
---
- Use matplotlib for low-level plotting control and customization.
- Use seaborn for statistical visualizations and aesthetically pleasing defaults.
- Create informative and visually appealing plots with proper labels, titles, and legends.
- Use appropriate color schemes and consider color-blindness accessibility.
- Create reusable plotting functions for consistent visualizations.---
description: Rules for creating informative and visually appealing plots using matplotlib and seaborn, with considerations for accessibility.
globs: **/visualization/*.py
---
- Use matplotlib for low-level plotting control and customization.
- Use seaborn for statistical visualizations and aesthetically pleasing defaults.
- Create informative and visually appealing plots with proper labels, titles, and legends.
- Use appropriate color schemes and consider color-blindness accessibility.
- Create reusable plotting functions for consistent visualizations.---
description: Governs error handling and data validation practices, including data quality checks, missing data handling, and data type validation.
globs: **/*.py
---
- Implement data quality checks at the beginning of analysis.
- Handle missing data appropriately (imputation, removal, or flagging).
- Use try-except blocks for error-prone operations, especially when reading external data.
- Validate data types and ranges to ensure data integrity.---
description: Applies general guidelines for data analysis, visualization, and Jupyter Notebook development with Python, focusing on best practices with pandas, matplotlib, and seaborn.
globs: **/*.ipynb
---
- Write concise, technical responses with accurate Python examples.
- Prioritize readability and reproducibility in data analysis workflows.
- Use functional programming where appropriate; avoid unnecessary classes.
- Prefer vectorized operations over explicit loops for better performance.
- Use descriptive variable names that reflect the data they contain.
- Follow PEP 8 style guidelines for Python code.
- Structure notebooks with clear sections using markdown cells.
- Use meaningful cell execution order to ensure reproducibility.
- Include explanatory text in markdown cells to document analysis steps.
- Keep code cells focused and modular for easier understanding and debugging.
- Use magic commands like %matplotlib inline for inline plotting.
- Document data sources, assumptions, and methodologies clearly.
- Use version control (e.g., git) for tracking changes in notebooks and scripts.
- Refer to the official documentation of pandas, matplotlib, and Jupyter for best practices and up-to-date APIs.---
description: Sets the convention to begin any analysis with data exploration and summary statistics, providing a consistent starting point.
globs: **/*.py
---
- Begin analysis with data exploration and summary statistics.---
description: Guidelines for structuring and documenting Jupyter notebooks for reproducibility and clarity.
globs: **/*.ipynb
---
- Structure notebooks with clear sections using markdown cells.
- Use meaningful cell execution order to ensure reproducibility.
- Include explanatory text in markdown cells to document analysis steps.
- Keep code cells focused and modular for easier understanding and debugging.
- Use magic commands like %matplotlib inline for inline plotting.
- Document data sources, assumptions, and methodologies clearly.
- Use version control (e.g., git) for tracking changes in notebooks and scripts.---
description: Specific optimization strategies for Python scripts working with larger-than-memory datasets via Dask.
globs: **/dask_analysis/*.py
---
- Consider using dask for larger-than-memory datasets.---
description: Focuses on pandas-specific rules for data manipulation, including method chaining, data selection using loc/iloc, and groupby operations.
globs: **/*.py
---
- Use pandas for data manipulation and analysis.
- Prefer method chaining for data transformations when possible.
- Use loc and iloc for explicit data selection.
- Utilize groupby operations for efficient data aggregation.---
description: Outlines rules for optimizing performance, including vectorized operations, efficient data structures, and profiling code for bottlenecks.
globs: **/*.py
---
- Use vectorized operations in pandas and numpy for improved performance.
- Utilize efficient data structures (e.g., categorical data types for low-cardinality string columns).
- Consider using dask for larger-than-memory datasets.
- Profile code to identify and optimize bottlenecks.---
description: General rules for Python data analysis and manipulation, emphasizing pandas, numpy, and vectorized operations.
globs: **/*.py
---
- Write concise, technical responses with accurate Python examples.
- Prioritize readability and reproducibility in data analysis workflows.
- Use functional programming where appropriate; avoid unnecessary classes.
- Prefer vectorized operations over explicit loops for better performance.
- Use descriptive variable names that reflect the data they contain.
- Follow PEP 8 style guidelines for Python code.
- Use pandas for data manipulation and analysis.
- Prefer method chaining for data transformations when possible.
- Use loc and iloc for explicit data selection.
- Utilize groupby operations for efficient data aggregation.
- Implement data quality checks at the beginning of analysis.
- Handle missing data appropriately (imputation, removal, or flagging).
- Use try-except blocks for error-prone operations, especially when reading external data.
- Validate data types and ranges to ensure data integrity.
- Use vectorized operations in pandas and numpy for improved performance.
- Utilize efficient data structures (e.g., categorical data types for low-cardinality string columns).
- Profile code to identify and optimize bottlenecks.# Pandas Scikit-Learn Guide .cursorrules prompt file

Author: Championeer

## What you can build
DataVis Studio: A web app that allows users to upload datasets and automatically generates visualizations using matplotlib and seaborn, with options for customization and accessibility considerations.Notebook Optimizer: A service that analyzes Jupyter Notebooks for performance bottlenecks, suggests code optimizations such as using vectorized operations, and checks adherence to PEP 8 guidelines.Pandas Playground: An interactive platform for learning and experimenting with pandas data manipulation through hands-on tutorials, with instant feedback and visualization of results using matplotlib and seaborn.Data Cleanse Pro: An application that assists users in implementing data validation and cleaning processes, providing automated suggestions for handling missing data and identifying data quality issues.Jupyter Notebook Template Generator: A tool that generates well-structured Jupyter Notebooks based on user-defined data analysis workflows, including sections for markdown documentation and pre-configured plotting functions.Dataset Profiler: A software that quickly provides summary statistics and insights on datasets, enabling users to start their analysis efficiently and understand potential data quality challenges.Visualization Style Guide App: A platform that offers predefined plotting templates and styles adhering to best practices, ensuring consistent aesthetics and accessibility in visualizations.Data Version Control System: A service that integrates with git, allowing users to manage and track changes in datasets and Jupyter Notebooks, facilitating collaboration and reproducibility.Python Performance Profiler: An application that profiles Python data analysis scripts, identifies slow segments, and provides suggestions for performance improvements using numpy and pandas.Dask Integration Dashboard: A tool that aids in setting up and managing Dask environments for handling large datasets, with visual monitoring of resource usage and task performance.

## Benefits


## Synopsis
Data scientists and analysts can use this prompt to create reproducible, high-performance analysis and visualization workflows in Jupyter Notebooks using Python libraries.

## Overview of .cursorrules prompt
The .cursorrules file outlines best practices and principles for data analysis, visualization, and Jupyter Notebook development with a focus on Python libraries such as pandas, matplotlib, seaborn, and numpy. It emphasizes writing concise and technical responses with accurate Python examples and promotes readability and reproducibility in data analysis workflows. It advocates for functional programming, vectorized operations, and descriptive variable names. The file also provides guidance on data manipulation using pandas, visualization with matplotlib and seaborn, and Jupyter Notebook organization. It includes recommendations for error handling, data validation, and performance optimization, and lists essential dependencies such as pandas, numpy, and scikit-learn. It encourages starting analysis with data exploration and documentation while using version control systems like git.

