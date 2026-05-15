# AdaMeZO

This is the official implementation of the paper: [AdaMeZO: Adam-style Zeroth-Order Optimizer for LLM Fine-tuning Without Maintaining the Moments](https://arxiv.org/abs/2605.00650). This implementation is heavily based on [MeZO](https://github.com/princeton-nlp/mezo). We are grateful to their fantastic work.

# Usage

To turn on AdaMeZO, use ```AMODE=1 HESS_WINDOW=10``` and specify ```BETA1``` and ```BETA2```.

Example usage:

```bash
cd MeZO/large_models

# # hessian lr=1e-7
CUDA_VISIBLE_DEVICES=0 SEED=0 NUMEXPR_MAX_THREADS=80 MODE=ft TASK=SST2 STEPS=40000 AMODE=1 HESS_WINDOW=10 BETA1=0.7 MU=0.99999 BETA2=0.9 LR=1.0e-7 MODEL=facebook/opt-1.3b nohup bash mezo.sh 

# mezo lr=1e-7
CUDA_VISIBLE_DEVICES=0 SEED=0 NUMEXPR_MAX_THREADS=80 MODE=ft TASK=SST2 STEPS=40000 AMODE=1 HESS_WINDOW=0 MU=0.99999 BETA2=0.9 LR=1.0e-7 MODEL=facebook/opt-1.3b nohup bash mezo.sh

# mezo lr=searching
searching_lr=1.7e-7 # example settings

CUDA_VISIBLE_DEVICES=0 SEED=0 NUMEXPR_MAX_THREADS=80 MODE=ft TASK=SST2 STEPS=40000 AMODE=1 HESS_WINDOW=0 MU=0.99999 BETA2=0.9 LR=$searching_lr MODEL=facebook/opt-1.3b nohup bash mezo.sh

```

# Citation

If you found our work interesting, we will be happy if you can cite our work using the following citation.

```
@inproceedings{cai2026adamezo,
  title     = {AdaMeZO: Adam-style Zeroth-Order Optimizer for LLM Fine-tuning Without Maintaining the Moments},
  author    = {Cai, Zhijie and Chen, Haolong and Zhu, Guangxu},
  booktitle = {Forty-third International Conference on Machine Learning},
  year      = {2026},
  note      = {To appear}
}
```