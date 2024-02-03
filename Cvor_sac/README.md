### Optimizing Gradient through CVor: A Universal Control Variates Operator

### Description

We have integrated the CVOR operator into the original SAC codebase, allowing for quick and easy usage through simple operations. Depending on the specific F function, CVOR may have different effects, and we encourage readers to design their own F functions.

------------
### Requirements
------------
*   [mujoco-py](https://github.com/openai/mujoco-py)
*   [PyTorch](http://pytorch.org/)

### Default Arguments and Usage
------------
### Usage

```
usage: main.py [-h] [--env-name ENV_NAME] [--policy POLICY] [--eval EVAL]
               [--gamma G] [--tau G] [--lr G] [--alpha G]
               [--automatic_entropy_tuning G] [--seed N] [--batch_size N]
               [--num_steps N] [--hidden_size N] [--updates_per_step N]
               [--start_steps N] [--target_update_interval N]
               [--replay_size N] [--cuda] [--cvor [BOOL]]
```

(Note: There is no need for setting Temperature(`--alpha`) if `--automatic_entropy_tuning` is True.)

#### For SAC

```
python main.py --env-name Humanoid-v2 --alpha 0.05 --cuda
python main.py --env-name Walker2d-v2 --alpha 0.2 --cuda
```

#### For SAC_cvor

```
python main.py --env-name Humanoid-v2 --alpha 0.05  --cuda --cvor True
python main.py --env-name Walker2d-v2 --alpha 0.2 --cuda --cvor True
```

### Arguments
------------
```
PyTorch Soft Actor-Critic Args

optional arguments:
  -h, --help            show this help message and exit
  --env-name ENV_NAME   Mujoco Gym environment (default: HalfCheetah-v2)
  --policy POLICY       Policy Type: Gaussian | Deterministic (default:
                        Gaussian)
  --eval EVAL           Evaluates a policy a policy every 10 episode (default:
                        True)
  --gamma G             discount factor for reward (default: 0.99)
  --tau G               target smoothing coefficient(τ) (default: 5e-3)
  --lr G                learning rate (default: 3e-4)
  --alpha G             Temperature parameter α determines the relative
                        importance of the entropy term against the reward
                        (default: 0.2)
  --automatic_entropy_tuning G
                        Automaically adjust α (default: False)
  --seed N              random seed (default: 123456)
  --batch_size N        batch size (default: 256)
  --num_steps N         maximum number of steps (default: 1e6)
  --hidden_size N       hidden size (default: 256)
  --updates_per_step N  model updates per simulator step (default: 1)
  --start_steps N       Steps sampling random actions (default: 1e4)
  --target_update_interval N
                        Value target update per no. of updates per step
                        (default: 1)
  --replay_size N       size of replay buffer (default: 1e6)
  --cuda                run on CUDA (default: False)
  --cvor       BOOL     Optimizing gradients using cvor          
```

| Environment **(`--env-name`)**| Temperature **(`--alpha`)**|
| ---------------| -------------|
| HalfCheetah-v2| 0.2|
| Hopper-v2| 0.2|
| Walker2d-v2| 0.2|
| Ant-v2| 0.2|
| Humanoid-v2| 0.05|

## Acknowledgement

The code is modified from SAC(https://github.com/pranz24/pytorch-soft-actor-critic)
