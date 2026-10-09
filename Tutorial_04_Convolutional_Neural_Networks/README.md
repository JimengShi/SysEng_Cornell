# Tutorial 04 · Convolutional Neural Networks

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_04_Convolutional_Neural_Networks/tutorial_04_cnn.ipynb)

MNIST dense/CNN comparison and CIFAR-10 regularization and augmentation.

**Runtime:** CPU quick mode; GPU optional. Open the notebook, connect, and select **Runtime → Run all**. Dependency setup is included. Each notebook runs independently without local files or earlier lessons.

Basic PyTorch training (Tutorial 03) is helpful. Quick mode trains two models on MNIST and three prespecified variants on CIFAR-10 for three epochs each. Data augmentation affects only training images. Results are saved in `outputs/tutorial_04/metrics.json`; short-run comparisons do not establish the best architecture or regularization strategy.

While the repository is private, direct Colab opening requires repository access and GitHub authorization. Downloading the notebook and uploading it to Colab is an alternative. See the [series README](../README.md) and [validation report](../docs/validation.md).

Adapted from the corresponding PEESE SYSEN tutorial under the repository MIT license; source and data references are included in the notebook.
