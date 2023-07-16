# Latent Diffusion Models
This repo is used as an example for training and finetuning [latent-diffusion](https://github.com/CompVis/latent-diffusion) used as the baseline in [StableSR](https://github.com/IceClear/StableSR).

## Requirements
A suitable [conda](https://conda.io/) environment named `ldm` can be created
and activated with:

```
conda env create -f environment.yaml
conda activate ldm
```

## Pretrained Models
You can download our finetuned model [here](https://huggingface.co/Iceclear/StableSR/resolve/main/ldmsr4x_finetune_119.ckpt).

## Train

```
python main.py --base configs/bsr_sr/config_sr_finetune.yaml -t --gpus 0, --train --scale_lr False
```

## Inference

We use eta=1.0 as a type of DDPM using the offical DDIM sampling code.

```
python scripts/sr_val_ddim_realsr.py --config configs/bsr_sr/config_sr_finetune.yaml --ckpt CKPT_PATH --outdir OUTPUT_PATH --skip_grid --ddim_steps 200 --init-img INPUT_PATH --ddim_eta 1.0 --color_fix
```

## Acknowledgement

This repo is an extension built on [latent-diffusion](https://github.com/openai/guided-diffusion).
Some codes are also borrowing from [BasicSR](https://github.com/XPixelGroup/BasicSR).
Thanks for open-sourcing!
