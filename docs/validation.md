# Tutorial 03 validation status

This report distinguishes checks performed from intended runtime support.

## Completed checks

- Notebook format validated with `nbformat` (33 cells, 17 code cells).
- Published notebook has unique cell IDs, no execution state, and no saved outputs.
- Auto MPG was downloaded from UCI and its SHA-256 checksum recorded.
- Reviewed training-only preprocessing, disjoint splits, sample-weighted losses, validation checkpoint selection, CPU/CUDA tensor placement, and checkpoint metadata.
- README and notebook include direct Colab links and in-notebook dependency installation.

## Execution status

End-to-end execution has not yet been verified. The initial local Jupyter attempt stopped before any notebook cells ran because the sandbox blocked the kernel's local ports. A rerun outside the sandbox was not performed.

CPU support, the quick/full modes, learning metrics, rendered plots, and checkpoint round trips remain pending runtime validation. The notebook includes the checks, but their presence does not mean they have passed. No measured runtime or model performance is claimed here.

## Reproduce a check

For a Colab check, follow the README badge, connect to a fresh CPU runtime, and select **Runtime → Run all**. Record the environment table, all final outputs, `outputs/tutorial_03/metrics.json`, and any error. GPU and full-data tests should be recorded separately.

For a local check, install `requirements-validation.txt` in a Python 3.12 virtual environment and run:

```bash
python scripts/validate_tutorial03.py --execute --cpu
```

The script uses a fresh kernel, saves an executed copy and plot images, and checks that the learned models beat simple sanity thresholds. An optional larger run is available with `--full --output-dir .validation/tutorial03-full`.
