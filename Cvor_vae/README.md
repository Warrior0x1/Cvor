# Optimizing Gradient through CVor: A Universal Control Variates Operator

## Dependencies
```
tensorflow >= 2.5.0
tensorflow-datasets >= 4.2.0
tensorflow-probability >= 0.12.2
scipy >= 1.6.3
absl >= 0.12.0
pandas >= 1.2.4
numpy >= 1.19.5
tqdm >= 4.60.0
```

## Usage
Running VAE experiments:
```
python experiment_launcher_singlelayer.py --dataset={dataset} --genmo_lr={lr} --infnet_lr={lr} --encoder_type=nonlinear --grad_type={grad_type} --K={K} --D=200 --seed={seed}
```

- `dataset`: 
  - dynamically binarized: `mnist`, `fashion_mnist`.
  - non-binarized: `continuous_fashion`.
- `lr`: 
  - dynamically binarized: `1e-3` for `mnist` , `3e-4` for `fashion_mnist`.
  - non-binarized: `1e-4`.
- `grad_type`: 
  - BASELINE:`reinforce`
  - REINFORCE leave-one-out: `reinforce_loo`
  - Double CV (Titsias & Shi, 2021): `double_cv`
  - RODEO (stein): 
    - `K=2`: `discrete_stein_avg`
    - `K>2`: `discrete_stein_output_avg`
  - Cvor_AO (ours):`Cvor_AO`
  - Cvor(ours)：`Cvor`


## Citation

To cite this work, please use
