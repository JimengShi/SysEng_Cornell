# Colab validation report

Validated on **2026-10-09** using Google Colab CPU runtimes. All five notebooks' default code paths passed sequential execution (55 code cells total). Published notebooks have cleared outputs and execution counts.

## How the checks were performed

Because this GitHub repository remains private and the browser's Colab session was not authorized for GitHub access, the exact notebook code-cell sources were read from the repository and placed into Colab verification notebooks. A harness executed each source in order using Colab's native IPython `run_cell`, stopping on any exception. SHA-256 hashes of the code cells joined with two newlines identify the tested sources in [the machine-readable record](validation-results.json).

Tutorial 03 ran separately. Tutorials 01, 02, and 04 ran sequentially in a shared runtime; Tutorial 05 was then verified separately after fixing its data source. This verifies actual code execution in Colab. It is not a claim that the private GitHub authorization flow or an imported five-notebook **Run all** workflow was tested. No GitHub authorization or repository visibility change was performed.

The initial generic IPython-shell harness failed at `%matplotlib inline`; using the native Colab shell resolved this harness issue. The original Google-hosted cats/dogs URL returned HTTP 403. Tutorial 05 now uses the PyTorch-hosted ants/bees teaching archive, and the revised default code passed all 11 cells.

## Recorded environment and results

Python **3.13.16**, PyTorch **2.11.0+cpu**, torchvision **0.26.0+cpu**, NumPy **2.1.3**, Pandas **2.2.3**, Matplotlib **3.10.0**. Tutorial 02 also used Seaborn **0.13.2** and Plotly **5.24.1**. Machine-learning runs used seed 42 and `QUICK_RUN=True`.

| Tutorial | Code cells | Observed result |
|---|---:|---|
| 01 | 8 | Five synthetic readings: total 55 kWh, mean 11 kWh; JSON save/reload passed. |
| 02 | 9 | 13 raw rows → 10 clean rows; total 222 kWh; CSV round trip and figure/HTML exports passed. |
| 03 | 17 | Validation-selected MLP: test MAE 1.917 MPG, RMSE 2.638 MPG (baseline RMSE 7.432). Fashion-MNIST test accuracy 81.75% (baseline 10%). Both checkpoint reload checks passed. |
| 04 | 10 | MNIST CNN test accuracy 92.2%; dense model 88.4%. Validation-selected CIFAR-10 Plain CNN: test accuracy 44.65% (baseline 10.2%). All five model runs completed. |
| 05 | 11 | Ants/bees: validation accuracy 95%, test accuracy 93.33% on 60 test images (baseline 50%); both-class Grad-CAM, model reload, and ViT shape checks passed. |

These are observed teaching runs, not benchmark guarantees. In Tutorial 04, three epochs did not make the augmented model outperform the plain model. In Tutorial 05, the archive is an ImageNet subset and the feature extractor was pretrained on ImageNet: these results do not demonstrate independence from pretraining data or generalization to a new domain.

CIFAR-10 downloading dominated Tutorial 04's approximately 22.6-minute recorded run; server speed varies. Quick mode reduces training, not the size of the source archive download. Tutorial 05's core run took about 29 seconds after imports on this runtime; this is not a promised duration.

The optional Tutorial 05 style-transfer branch also passed on CPU with `RUN_STYLE_TRANSFER=True`: 128 × 128 pixels, 40 optimization steps, finite losses throughout, and a loss decrease from 454,754.125 to 35,324.152. This branch was run separately after the core lesson. The saved Grad-CAM and style-transfer images were displayed in Colab and visually inspected.

## Scope and remaining limits

- CPU quick-mode code execution was tested. GPU execution and larger `QUICK_RUN=False` experiments were not tested.
- All required packages were already installed in the tested Colab runtimes. Missing-package installation branches were reviewed, but were not exercised in a stripped runtime.
- Runtime data and trained weights are not committed. Notebook assertions check splits, shapes, finite values, or checkpoint equality where relevant.
- Local notebook execution was not performed after the initial sandbox kernel restriction. Local package installation is not counted as runtime validation.
- Colab resources, installed package versions, and upstream download availability can change. If a runtime has unrelated package modifications, start a fresh runtime before running the lesson.

## Reproduce

Open a lesson in Colab, connect to a fresh CPU runtime, and run cells in order. For a private repository, authorize access or upload the downloaded notebook. Save the final outputs and environment information, plus `outputs/tutorial_XX/metrics.json` (Tutorial 01 uses `energy_summary.json`). Test full/GPU/optional modes separately and record their settings.

From a local environment containing `nbformat` and IPython, `python scripts/check_notebooks.py` checks all five notebooks' schema, unique IDs, cleared outputs, Python/IPython syntax, and Colab targets without starting kernels. The optional `scripts/validate_tutorial03.py --execute --cpu` runner executes Tutorial 03 in a fresh local kernel and saves results under `.validation/`; this was not the method used for the Colab results above.
