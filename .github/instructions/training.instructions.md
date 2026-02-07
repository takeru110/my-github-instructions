---
applyTo: "src/**/train/**/*.py"
---

# Training instructions

## Training
- Use a train-test split (90/10) or cross-validation as appropriate; log which strategy is used and why.
- Ensure reproducibility:
  - Set and log random seeds when randomness is involved.
  - Log key run parameters (excluding secrets).

## Hyperparameter optimization (when required)
- If hyperparameter search is required, use `hydra-optuna-sweeper`.
- Training scripts must use the `@hydra.main()` entry point when using Hydra.
- Define search space in `config.yaml` using Optuna syntax (example):
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
