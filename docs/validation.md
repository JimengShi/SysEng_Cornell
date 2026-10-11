# Colab validation report

Tutorials 01–06 were validated on **2026-10-09**, Tutorial 07 on **2026-10-10**, and Tutorial 08 on **2026-10-11**, using Google Colab CPU runtimes. All eight notebooks’ default code paths passed sequential execution (96 code cells total). Published notebooks have cleared outputs and execution counts.

## How the checks were performed

Because this GitHub repository remains private and the browser's Colab session was not authorized for GitHub access, the exact notebook code-cell sources were read from the repository and placed into Colab verification notebooks. A harness executed each source in order using Colab's native IPython `run_cell`, stopping on any exception. SHA-256 hashes of the code cells joined with two newlines identify the tested sources in [the machine-readable record](validation-results.json).

Tutorial 03 ran separately. Tutorials 01, 02, and 04 ran sequentially in a shared runtime; Tutorial 05 was then verified separately after fixing its data source. This verifies actual code execution in Colab. It is not a claim that the private GitHub authorization flow or an imported five-notebook **Run all** workflow was tested. No GitHub authorization or repository visibility change was performed.

The initial generic IPython-shell harness failed at `%matplotlib inline`; using the native Colab shell resolved this harness issue. The original Google-hosted cats/dogs URL returned HTTP 403. Tutorial 05 now uses the PyTorch-hosted ants/bees teaching archive, and the revised default code initially passed all 11 cells. The later ViT expansion increased Tutorial 05 to 16 code cells.

## Tutorial 05 ViT expansion: direct Run all verification

The expanded notebook was opened directly from GitHub commit `e0fde9f23c7c8c9b622e30fc16d08f8f47078d3e` in Colab and run with **Runtime → Run all** in a fresh CPU runtime. All 16 code cells completed without errors. The downloaded executed notebook matched that commit's code sources exactly. After inspecting the four rendered figures, the patch-sequence figure height/layout was adjusted to separate its titles, and Markdown approximation signs were clarified. These presentation-only adjustments were not rerun; both executed and published code hashes are recorded in the JSON. This later check supersedes the earlier harness-only limitation for Tutorial 05; it does not imply direct-opening tests for the other four lessons.

The expanded section compares the input image, numbered patch grid, patch sequence, pixel-vector and embedding heatmaps, positional embeddings, and untrained attention. Checks passed for exact image reconstruction (maximum error 0), convolution/linear projection equivalence, model forward equivalence, and attention row sums. Shapes were `[1,16,192]` for patches, `[1,16,64]` for projected tokens, and `[1,17,64]` after CLS/positions. The default full-notebook run took 35.15 seconds after imports on this runtime. The optional style branch was not rerun because its code was unchanged; its earlier evidence remains recorded.

## Tutorial 06: CPU execution verified

After the user freed Colab sessions, all 14 exact published code-cell sources executed sequentially in a fresh CPU runtime with Colab’s native `run_cell` harness. The downloaded verification notebook confirms exact source equality, no error outputs, and `ALL_14_CELLS_PASSED`. Four rendered figures (classes, learning curves, test comparison/confusion matrix, and predictions) were visually inspected. Direct GitHub opening required authorization and browser upload was unavailable; this check validates code execution, not the direct-opening or full notebook import workflow. No permissions or repository visibility were changed.

The flower archive and pretrained weights downloaded successfully. All assertions passed: disjoint splits, frozen backbone parameters and buffers, preserved head at unfreezing, unchanged protected fine-tuning state, changed unfrozen weights, cached/direct prediction equivalence, and CPU checkpoint reload. Quick mode used 200/50/50 images, 20 head epochs, and two fine-tuning epochs. Validation loss selected head epoch 11 and fine-tuning epoch 1. Trainable parameters increased from 6,405 to 892,485.

Frozen-feature validation/test accuracy was 82%/90%; fine-tuned accuracy was 84%/88%, against a 20% test baseline. Validation selected the fine-tuned model; its lower test accuracy is retained without retuning on the test set. With only 50 test images, the two-percentage-point difference is one image, not evidence of a general ranking. Fine-tuning is not guaranteed to improve test accuracy. ImageNet pretraining overlap was not audited.

Observed time after imports was 75.34 seconds, including 13.50 seconds caching, 0.35 seconds head fitting, and 35.32 seconds fine-tuning. Timings are observations, not guarantees or energy measurements. Full mode and GPU execution remain untested.

## Tutorial 07: detection, segmentation, and training verified

All 11 exact published code-cell sources ran sequentially in a fresh Colab CPU runtime using the native `run_cell` harness. The downloaded verification notebook was checked against the published sources, contained no error outputs, and ended with `ALL_11_CELLS_PASSED`. This checks real Colab execution, including installation of pinned **Ultralytics 8.4.158**, but does not establish direct GitHub authorization or full notebook import. Its Python/PyTorch environment matches the versions listed below.

The run downloaded YOLO11 nano detection and segmentation weights (5.4/5.9 MB) and COCO8. At image size 320, confidence 0.35, and NMS IoU 0.5, the bundled bus image produced four detections and four instance masks of shape `[4,1080,810]`. Coordinate/score bounds, original-resolution mask alignment, empty-result handling, unchanged background pixels, hand-computed IoU/NMS, and CSV/NPZ round trips all passed. Confidence cutoffs 0.2/0.5/0.8 yielded 5/4/3 instances at both tested NMS cutoffs; the synthetic overlapping-box example separately verified actual NMS suppression.

Default `RUN_TRAINING=True` completed two epochs on four training and four validation images. Label audits and train/validation hash separation passed; training losses were finite; `best.pt` reloaded and produced valid detection output. Five figures were inspected: input/boxes/masks, binary mask, synthetic NMS, ground-truth annotations, and training losses. COCO8 comes from COCO training data, so these are pipeline checks, not independent generalization results; reported validation mAP is retained only as diagnostic evidence.

The observed run took about 36 seconds including setup/imports; the notebook measured 18.28 seconds after imports and 10.22 seconds for training/checkpoint verification. These are not promised durations. A harmless config-directory warning caused Ultralytics to use `/tmp/Ultralytics`; execution and all exports succeeded. GPU, longer/custom-dataset training, segmentation training, and the optional training-skip branch were not separately tested.

## Tutorial 08: text classification and Skip-gram verified

All 11 exact published code-cell sources passed sequential execution using Colab's native `run_cell` harness on CPU. An initial fresh-runtime run downloaded the approximately 84 MB IMDb archive. After improving figure contrast and label placement, all cells were rerun in the same runtime with cached data. The final downloaded verification notebook matched the published sources exactly and contained no error outputs. Five rendered figures were inspected. This validates code execution, not direct private-GitHub authorization or full notebook import.

Exact-text deduplication yielded 5,994/998/1,995 training/validation/test reviews. Training-only vocabulary and IDF, one-hot/embedding equivalence, padding invariance, empty input, disjoint paths, finite losses, word/vector TSV alignment, and CPU checkpoint reload checks passed. The masked-embedding classifier completed eight epochs; validation loss selected epoch 5. Test accuracy was 80.85% versus 84.21% for TF-IDF and 49.97% for the training-majority baseline. Validation log loss selected the neural model, even though TF-IDF had higher accuracy; these are different criteria.

Skip-gram trained on 40,000 positive pairs sampled from 1,000 training reviews, using five noise samples and three epochs. Mean loss fell from 3.7249 to 2.4941. Many nearest neighbors remain poor: loss reduction and PCA plots do not demonstrate useful semantic representations. TSV exports contained 7,998 sentiment vectors and 4,194 observed Skip-gram target vectors. Full-data mode and GPU execution were not tested.

## Recorded environment and results

Python **3.13.16**, PyTorch **2.11.0+cpu**, torchvision **0.26.0+cpu**, NumPy **2.1.3**, Pandas **2.2.3**, Matplotlib **3.10.0**. Tutorial 02 also used Seaborn **0.13.2** and Plotly **5.24.1**. Machine-learning runs used seed 42 and `QUICK_RUN=True`.

| Tutorial | Code cells | Observed result |
|---|---:|---|
| 01 | 8 | Five synthetic readings: total 55 kWh, mean 11 kWh; JSON save/reload passed. |
| 02 | 9 | 13 raw rows → 10 clean rows; total 222 kWh; CSV round trip and figure/HTML exports passed. |
| 03 | 17 | Validation-selected MLP: test MAE 1.917 MPG, RMSE 2.638 MPG (baseline RMSE 7.432). Fashion-MNIST test accuracy 81.75% (baseline 10%). Both checkpoint reload checks passed. |
| 04 | 10 | MNIST CNN test accuracy 92.2%; dense model 88.4%. Validation-selected CIFAR-10 Plain CNN: test accuracy 44.65% (baseline 10.2%). All five model runs completed. |
| 05 | 16 | Ants/bees: validation accuracy 95%, test accuracy 93.33% on 60 test images (baseline 50%); both-class Grad-CAM, model reload, and ViT shape checks passed. |
| 06 | 14 | Frozen features: test accuracy 90%; fine-tuned: 88% on 50 images (baseline 20%). All freezing, fine-tuning, and checkpoint assertions passed. |
| 07 | 11 | Four detections/four masks; five figures inspected; IoU/NMS, coordinate/mask, empty-result, export, two-epoch training, and checkpoint inference checks passed. |
| 08 | 11 | IMDb neural/TF-IDF test accuracy 80.85%/84.21%; three Skip-gram epochs; five figures, padding, TSV, and checkpoint checks passed. |

These are observed teaching runs, not benchmark guarantees. In Tutorial 04, three epochs did not make the augmented model outperform the plain model. In Tutorial 05, the archive is an ImageNet subset and the feature extractor was pretrained on ImageNet: these results do not demonstrate independence from pretraining data or generalization to a new domain.

CIFAR-10 downloading dominated Tutorial 04's approximately 22.6-minute recorded run; server speed varies. Quick mode reduces training, not the size of the source archive download. Tutorial 05's core run took about 29 seconds after imports on this runtime; this is not a promised duration.

The optional Tutorial 05 style-transfer branch also passed on CPU with `RUN_STYLE_TRANSFER=True`: 128 × 128 pixels, 40 optimization steps, finite losses throughout, and a loss decrease from 454,754.125 to 35,324.152. This branch was run separately after the core lesson. The saved Grad-CAM and style-transfer images were displayed in Colab and visually inspected.

## Scope and remaining limits

- CPU quick-mode code execution was tested for Tutorials 01–08 (Tutorial 07 includes its default two-epoch smoke test). GPU execution and larger `QUICK_RUN=False` experiments were not tested.
- Tutorials 01–06 and 08 found their required packages already installed. Tutorial 07 exercised its pinned Ultralytics installation in Colab. Other missing-package branches were not exhaustively tested in stripped runtimes.
- Runtime data and trained weights are not committed. Notebook assertions check splits, shapes, finite values, or checkpoint equality where relevant.
- Local notebook execution was not performed after the initial sandbox kernel restriction. Local package installation is not counted as runtime validation.
- Colab resources, installed package versions, and upstream download availability can change. If a runtime has unrelated package modifications, start a fresh runtime before running the lesson.

## Reproduce

Open a lesson in Colab, connect to a fresh CPU runtime, and run cells in order. For a private repository, authorize access or upload the downloaded notebook. Save the final outputs and environment information, plus `outputs/tutorial_XX/metrics.json` (Tutorial 01 uses `energy_summary.json`). Test full/GPU/optional modes separately and record their settings.

From a local environment containing `nbformat` and IPython, `python scripts/check_notebooks.py` checks all eight notebooks' schema, unique IDs, cleared outputs, Python/IPython syntax, and Colab targets without starting kernels. The optional `scripts/validate_tutorial03.py --execute --cpu` runner executes Tutorial 03 in a fresh local kernel and saves results under `.validation/`; this was not the method used for the Colab results above.
