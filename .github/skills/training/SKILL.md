```skill
---
name: training
description: Guidelines and templates for ML training scripts with Hydra configuration and hyperparameter optimization using Optuna.
license: MIT
---

Guidelines and templates for ML training scripts with Hydra configuration and hyperparameter optimization using Optuna.

# SKILL: Training Script Guidelines

## Overview
Best practices for implementing reproducible ML training scripts with proper configuration management.

## Training
- Use a train-test split (90/10) or cross-validation as appropriate; log which strategy is used and why.
- Ensure reproducibility:
  - Set and log random seeds when randomness is involved.
  - Log key run parameters (excluding secrets).

## Hyperparameter optimization (when required)
- If hyperparameter search is required, use `hydra-optuna-sweeper`.
- Training scripts must use the `@hydra.main()` entry point when using Hydra.
- Define search space in `config.yaml` using Optuna syntax.

## Template Code

### Hydra Config Example (`config.yaml`)

```yaml
hydra:
  sweeper:
    _target_: hydra_plugins.hydra_optuna_sweeper.optuna_sweeper.OptunaSweeper
    direction: minimize  # or maximize
    n_trials: 100
    n_jobs: 1
    params:
      model.learning_rate: tag(log, interval(0.0001, 0.01))
      model.batch_size: choice(16, 32, 64, 128)
      model.num_layers: interval(2, 6)
```

### Training Script Entry Point Example

```python
import hydra
from omegaconf import DictConfig

@hydra.main(config_path=".", config_name="config", version_base=None)
def main(cfg: DictConfig) -> float:
    # Set random seed for reproducibility
    import random
    import numpy as np
    random.seed(cfg.seed)
    np.random.seed(cfg.seed)
    
    # Log run parameters
    import logging
    logger = logging.getLogger(__name__)
    logger.info(f"Running with config: {cfg}")
    
    # Training logic here
    ...
    
    return metric  # Return metric for Optuna optimization

if __name__ == "__main__":
    main()
```

## Key Points
- Always set and log random seeds for reproducibility.
- Use Hydra for configuration management.
- Use `hydra-optuna-sweeper` for hyperparameter optimization.
- Log key run parameters (excluding secrets).
- Training scripts should return the optimization metric.

```
