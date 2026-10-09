# Tutorial 05 · CNNs in Practice

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_05_CNN_in_Practice/tutorial_05_cnn_practice.ipynb)

Transfer learning, feature maps, Grad-CAM, optional neural style transfer, and a tiny ViT shape demo.

**Runtime:** CPU core lesson; optional style transfer is heavier. Open the notebook, connect, and select **Runtime → Run all**. Dependency setup is included. Each notebook runs independently without local files or earlier lessons.

Basic CNN concepts (Tutorial 04) are helpful. The core lesson trains a new classification head using frozen MobileNetV2 features, inspects filters and activations, computes Grad-CAM, and verifies a saved model. Outputs go to `outputs/tutorial_05/`. Grad-CAM is a model diagnostic, not a causal explanation.

**Optional style transfer:** `RUN_STYLE_TRANSFER = False` by default. Enabling it downloads about 550 MB of VGG19 weights; quick mode optimizes a 128-pixel image for 40 steps. The final tiny ViT uses random weights only to explain patch/token/logit shapes.

While the repository is private, direct Colab opening requires repository access and GitHub authorization. Downloading the notebook and uploading it to Colab is an alternative. See the [series README](../README.md) and [validation report](../docs/validation.md).

Adapted from the corresponding PEESE SYSEN tutorial under the repository MIT license; source and data references are included in the notebook.
