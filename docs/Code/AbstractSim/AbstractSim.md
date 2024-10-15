---
layout: default
title: "AbstractSim"
parent: "Code"
nav_order: 5
---
<details open markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

# AbstractSim

AbstractSim is a low-fidelity, 2D soccer simulation developed by the BadgerRL lab. It is written in Python and uses [StableBaselines3](https://stable-baselines3.readthedocs.io/en/master/) and the PettingZoo [Parallel API](https://pettingzoo.farama.org/api/parallel/) for RL training. 

## Installation

It is recommended to create a Python [virtual environment](https://docs.python.org/3/library/venv.html) using the provided `requirements.txt`  file. *You must use Python 3.9.*

```
python -m venv env
source env/bin/activate
python -m pip install -r requirements.txt
```

Alternatively, a shell script is provided for setting up a `conda` environment.

## Usage

### Training Policies

To train a policy, run the following command:

```bash
python run.py --train --env=<env name>
```

| Flags (Optional) | Description |
| --- | --- |
| `--batch_size=64` | Set the batch size. |
| `--vec_envs=12` | Sets the number of SB3 vectorized envs. |
| `--wandb` | Enable W&B. Must have W&B initialized to use. |
| `--total_timesteps=10000000` | Sets the number of training steps. |

### Visualizing Policies

To render a policy, run the following command:

```bash
# policy path is relative to the top-level directory
python run.py --render --env=<env name> --policy_path=<path to policy>
```

If no policy is provided, the environment will be rendered with randomly sampled actions.

### Exporting Policies

The `export.py` script can be used to convert a SB3 `.zip` policy into a format that is compatible with WisTex-United-system. From the top-level directory, run the following command:

```
# policy path is relative to the top-level directory
python export.py <path to policy>
```

The exported `.onnx` policy will be located in the `exported` folder. This file should then be moved into the `Config/Policies/` folder in WisTex-United-system.

## Development

Before creating your own environments, it is recommended to obtain a basic understanding of partially observable stochastic games (POSG) and how they are implemented by the [PettingZoo Parallel API](https://pettingzoo.farama.org/api/parallel/).