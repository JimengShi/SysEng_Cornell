# Deep Learning Tutorials · PyTorch on Colab

Learn to build, evaluate, and understand neural networks through practical notebooks. This independently maintained series adapts the [PEESE SYSEN 5888/6888 materials](https://github.com/PEESEgroup/SysEn6888) for public, self-contained use in Google Colab.

## Start learning

Run the tutorial directly in your browser—no local installation is needed: [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_03_PyTorch_Regression_and_Classification/tutorial_03_pytorch.ipynb).

| Tutorial | What you will build | Runtime | Open |
|---|---|---|---|
| **03 · Regression and Classification** | Fuel economy predictors and a clothing image classifier | CPU supported; GPU optional; no API key | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_03_PyTorch_Regression_and_Classification/tutorial_03_pytorch.ipynb) |

1. Click **Open in Colab** and connect to a runtime.
2. Optionally save your own copy through **File → Save a copy in Drive**.
3. Use **Runtime → Run all**, or work through cells in order.

The first code cell installs any missing packages **inside the Colab runtime**. You do not need to clone this repository, install Python locally, mount Google Drive, or complete another notebook first. The default quick run uses a small training set. Dataset downloads require internet access. Colab resources vary; a GPU is not required for Tutorial 03.

**Prerequisites:** basic Python and arrays. The notebook is written in English and includes explanations, results interpretation, exercises, and troubleshooting. Allow about 45–60 minutes for reading and exercises; see the [validation status](docs/validation.md) for checks performed and remaining limitations.

## Current release

**Tutorial 03 is the first released sample.** It covers tensors and gradients, train/validation/test splits, training-only standardization, linear and neural regression, classification with logits, baseline comparisons, confusion matrices, and checkpoint round trips.

The remaining PyTorch and framework-independent tutorials are planned for later adaptation. They are not included or advertised as verified in this release. TensorFlow versions are outside this series' current scope.

- [Tutorial details](Tutorial_03_PyTorch_Regression_and_Classification/README.md)
- [Validation evidence and limits](docs/validation.md)
- [Guidelines for future tutorials](CONTRIBUTING.md)

## Attribution and license

Adapted from [PEESEgroup/SysEn6888](https://github.com/PEESEgroup/SysEn6888) at revision `0b326ded95e415d7a60660879aaa737e3c7d79ea`. The original MIT copyright and permission notice are preserved in [LICENSE](LICENSE). This repository is an independent adaptation, not an official replacement for the course repository.

Dataset attribution appears in the notebook: [UCI Auto MPG](https://doi.org/10.24432/C5859H) (CC BY 4.0) and [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) (MIT). Datasets are downloaded from their sources and are not committed here.
