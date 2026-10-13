# Tutorial 12 · Deep Reinforcement Learning

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/JimengShi/SysEng_Cornell/blob/main/Tutorial_12_Deep_Reinforcement_Learning/tutorial_12_pytorch.ipynb)

Run from the top in Colab. The notebook installs missing packages, uses PyTorch and Gymnasium, and renders policy GIFs without Xvfb or local setup. No datasets, Atari ROMs, API keys, or Drive mount are required. Private GitHub links require access; alternatively upload the downloaded notebook to Colab.

## Included workflows

- CartPole-v1 stochastic actor–critic with bootstrapped episodic returns and a detached learned baseline.
- Pendulum-v1 DDPG with replay, bounded continuous actions, exploration, and soft target updates.
- Simplex-constrained synthetic materials composition control, using DDPG and an analytic baseline.
- Separate evaluation seeds, random/initial/simple baselines, seven plots, two policy GIFs, and nine CPU network reload checks.

Quick mode uses 240 CartPole episodes, 6,000 Pendulum steps, 4,000 materials steps, and 10 evaluation seeds per policy. CPU is supported; expect several minutes, with actual timing depending on the runtime. `QUICK_RUN=False` increases training/evaluation budgets. GPU is selected automatically when available.

## Interpretation

Short runs verify algorithms and interfaces; they do not guarantee solved environments or robust policies. Only one training seed per task is used by default. The materials task is a known-target numerical example, not physical material discovery. DQN/Atari and PPO are conceptual extensions, matching their outline-only status in the upstream PyTorch notebook.

Outputs are saved in `outputs/tutorial_12/`. Checkpoints are for inference/inspection rather than exact training resumption. See [validation evidence and tested modes](../docs/validation.md).

Adapted from [PEESE Tutorial 12](https://github.com/PEESEgroup/SysEn6888/tree/0b326ded95e415d7a60660879aaa737e3c7d79ea/Tutorial_12_Deep_Reinforcement_Learning); attribution is retained in [LICENSE](../LICENSE).
