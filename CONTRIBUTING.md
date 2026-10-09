# Maintaining the Colab tutorial series

Tutorial 03 is the template for future PyTorch and framework-independent lessons.

Each released notebook should:

1. State its question, prerequisites, learning goals, runtime requirements, and any costs.
2. Include a working Colab badge, all imports, dependency setup, and automatic public-data loading.
3. Run from a fresh runtime in cell order without local files, hidden state, personal credentials, or earlier notebooks.
4. Provide a small default example and explicitly label heavier optional experiments.
5. Explain tensor shapes, losses, units, baselines, and limitations of the results.
6. Fit preprocessing only on training data and use validation data for model selection.
7. Include interpretation prompts and exercises that do not break Run all.
8. Record actual validation evidence, versions, device, and tested modes. Local execution must not be labeled as a live Colab test.
9. Preserve upstream attribution and dataset licenses; never commit API keys, downloaded datasets, or large checkpoints.

For Tutorial 03, run `python scripts/validate_tutorial03.py --execute --cpu` after edits. Review the saved plots and metrics, update `docs/validation.md`, and keep notebook outputs cleared before publishing. Dependencies in `requirements-validation.txt` describe a prepared local environment; the notebook intentionally uses Colab's installed packages unless a required package is missing.
