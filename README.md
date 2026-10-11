# Deep Learning Tutorials · PyTorch on Colab

Learn Python, data analysis, and neural networks through ten self-contained notebooks. This independently maintained series adapts the [PEESE SYSEN 5888/6888 materials](https://github.com/PEESEgroup/SysEn6888) for Google Colab. Lessons are written in English; deep-learning examples use PyTorch.

## Start learning

Click a badge to open a notebook in Colab. No local Python installation or repository clone is needed.

| Tutorial | What you will learn | Open |
|---|---|---|
| **[01 · Colab and Python Basics](Tutorial_01_Colab_and_Python_Basics/README.md)** | Python types, collections, control flow, functions, and a synthetic energy summary | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_01_Colab_and_Python_Basics/tutorial_01_python.ipynb) |
| **[02 · NumPy, Pandas, and Visualization](Tutorial_02_NumPy_Pandas_and_Visualization/README.md)** | Arrays, data cleaning, aggregation, static plots, and interactive Plotly charts | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_02_NumPy_Pandas_and_Visualization/tutorial_02_data.ipynb) |
| **[03 · Regression and Classification](Tutorial_03_PyTorch_Regression_and_Classification/README.md)** | Auto MPG regression and Fashion-MNIST classification with PyTorch | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_03_PyTorch_Regression_and_Classification/tutorial_03_pytorch.ipynb) |
| **[04 · Convolutional Neural Networks](Tutorial_04_Convolutional_Neural_Networks/README.md)** | MNIST dense/CNN comparison and CIFAR-10 regularization and augmentation | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_04_Convolutional_Neural_Networks/tutorial_04_cnn.ipynb) |
| **[05 · CNNs in Practice](Tutorial_05_CNN_in_Practice/README.md)** | Transfer learning, feature maps, Grad-CAM, optional neural style transfer, and a visual ViT image-to-token walkthrough | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_05_CNN_in_Practice/tutorial_05_cnn_practice.ipynb) |
| **[06 · Transfer Learning](Tutorial_06_Transfer_Learning/README.md)** | Pretrained inference, frozen features versus fine-tuning, parameter audits, and five-class flower classification | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_06_Transfer_Learning/tutorial_06_pytorch.ipynb) |
| **[07 · Object Detection and Segmentation](Tutorial_07_Object_Detection_and_Segmentation/README.md)** | YOLO11 boxes, instance masks, NMS/threshold experiments, exports, and a tiny detection training workflow | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_07_Object_Detection_and_Segmentation/tutorial_07_pytorch.ipynb) |
| **[08 · Text and Word Embeddings](Tutorial_08_Text_and_Sequences/README.md)** | Tokenization, masked-pooling sentiment, TF-IDF, Skip-gram negative sampling, embedding visualization and export | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_08_Text_and_Sequences/tutorial_08_pytorch.ipynb) |
| **[09 · Encoder–Decoder Transformers](Tutorial_09_Transformers_Implementation/README.md)** | Positions, self/cross-attention, causal masks, Spanish–English training and autoregressive translation | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_09_Transformers_Implementation/tutorial_09_pytorch.ipynb) |
| **[10 · Autoencoders and VAEs](Tutorial_10_Generative_Modeling_VAE/README.md)** | Reconstruction, denoising, ECG anomaly scoring, VAE latent exploration, and shared-encoder adversarial training | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_10_Generative_Modeling_VAE/tutorial_10_pytorch.ipynb) |

1. Open a notebook and connect to a runtime. A CPU is sufficient for the default examples.
2. Optionally choose **File → Save a copy in Drive** to keep your changes.
3. Choose **Runtime → Run all**, or work through the cells in order. Setup cells install missing packages inside Colab.
4. Read the explanations and try the exercises after the initial run. Each lesson can run independently; following 01 → 10 is recommended for beginners.

**Private-repository access:** This repository is currently private. Direct Colab links require repository access and GitHub authorization in Colab. “Notebook not found” may indicate missing authorization. Alternatively, download an `.ipynb` file from GitHub and use **File → Upload notebook** in Colab. The badges do not make a private repository publicly accessible.

## Runtime and data

- **01:** Python standard library only; no package installation or external data.
- **02:** NumPy, Pandas, Matplotlib, Seaborn, and Plotly; data are embedded and explicitly synthetic.
- **03:** Auto MPG and Fashion-MNIST download automatically. The default quick run uses 6,000 Fashion-MNIST training images.
- **04:** MNIST and CIFAR-10 download automatically (CIFAR-10 archive about 163 MB). Quick mode uses small subsets and three epochs per model. The full archive is still downloaded; the official server can take 20 minutes or more.
- **05:** Ants/bees archive (about 45 MB) and pretrained MobileNetV2 weights (about 14 MB) download automatically. Frozen features keep the core lesson practical on CPU. Neural style transfer is **off by default**: enabling `RUN_STYLE_TRANSFER` downloads VGG19 weights (about 550 MB) and performs a separate optimization. The tiny Vision Transformer section compares images, patch sequences, numeric embeddings, positional information, and untrained attention; it does not train a classifier.
- **06:** Flowers archive (about 218 MB) and MobileNetV2 weights (about 14 MB) download automatically. Quick mode uses 200/50/50 train/validation/test images, 20 cached-feature head epochs, and two image-based fine-tuning epochs.
- **07:** Pinned Ultralytics/YOLO11 setup, bundled example image, about 12 MB of nano model weights, and a roughly 1 MB COCO8 download. The default includes two CPU-compatible detection training epochs; set `RUN_TRAINING=False` to skip them. COCO8 is a workflow smoke test, not an independent benchmark.
- **08:** IMDb archive (about 84 MB), with balanced subsets and exact-text deduplication. Eight sentiment epochs and three Skip-gram epochs run by default; includes TF-IDF comparison, embedding plots, TSV exports, and checkpoint reload.
- **09:** A 2.6 MB Spanish–English archive; 3,000/400/400 short pairs and six Transformer training epochs in quick mode. Includes token/position/attention plots, teacher-forced and greedy evaluation, and CPU checkpoint reload.
- **10:** Fashion-MNIST, MNIST, and ECG downloads (~50 MB). CPU-friendly AE/denoising, normal-only anomaly fitting, a 2D VAE, and a two-epoch shared-encoder AAE demonstration. Includes ten figures, a fixed-prior training GIF, and five checkpoint reloads.

For 03–06 and 08–10, `QUICK_RUN = True` is the default. Set it to `False` for larger experiments. `DEVICE_PREFERENCE = "auto"` uses a GPU when available and otherwise CPU; select `"cpu"` to force CPU. Downloads require internet access; no API key or Google Drive mount is required. Colab runtime files are temporary: download anything you want to keep from `outputs/tutorial_XX/` before disconnecting.

The notebooks retain installed Colab packages and install only missing dependencies. They print their environment versions. All ten default code paths passed sequential execution in Colab CPU runtimes. See [validation evidence and limits](docs/validation.md) for the exact tests performed; quick-mode results are teaching examples, not benchmark claims.

## Teaching approach

Each lesson includes learning goals, explanations, runnable examples, interpretation prompts, and exercises. The classification/regression lessons separate training, validation, and test data and select models using validation results. Tutorial 07 explicitly uses a tiny training/validation smoke test with no independent test claim. Tutorial 03 includes regression and classification checkpoint round trips; Tutorials 05 and 06 save and reload their transfer-learning models.

- [Validation evidence](docs/validation.md)
- [Contribution guidelines](CONTRIBUTING.md)

## Attribution and license

Adapted from [PEESEgroup/SysEn6888](https://github.com/PEESEgroup/SysEn6888) at revision `0b326ded95e415d7a60660879aaa737e3c7d79ea`. The original MIT notice is preserved in [LICENSE](LICENSE). This is an independent adaptation, not an official replacement for the course repository. TensorFlow versions are outside this series' scope.

Data and pretrained model sources are attributed in the notebooks. These include [UCI Auto MPG](https://doi.org/10.24432/C5859H), [Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist), MNIST, CIFAR-10, the PyTorch-hosted ants/bees archive, Google flower photos, ManyThings/Tatoeba bilingual pairs, the Google-hosted ECG CSV, COCO8, [Stanford IMDb](https://ai.stanford.edu/~amaas/data/sentiment/), torchvision model weights, and Ultralytics YOLO11 weights/example assets. The code license does not replace their respective terms. Datasets and model weights are downloaded from their sources and are not committed here.
