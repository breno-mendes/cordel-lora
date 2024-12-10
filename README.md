# Cordel Flux Lora

The LoRA Cordel files (lora.safetensor) as well as the configuration file (config.yaml) can be found in the [HuggingFace repository](https://huggingface.co/brenomendes/cordel-flux-lora). You can download the simpler LoRA trained on parameter lora rank 16, which produces results closer to the Cordel style, using the lora.safetensors file. If you are looking for a model capable of generating more complex images resembling the Cordel style, opt for the model trained with parameter lora rank set on 32 found within the compressed file lora_2.tar.

The models can be used on online platforms like Replicate and HuggingFace. If you wish to run the LoRA Cordel locally, make sure to download the base model [Flux.1 dev](https://huggingface.co/black-forest-labs/FLUX.1-dev/tree/main) from the Black Forest Labs repository.

<!-- <Gallery /> -->

Trained on Replicate using:

https://replicate.com/ostris/flux-dev-lora-trainer/train

## Trigger words

You should use `CORDEL` to trigger the image generation.

## Use it with the [🧨 diffusers library](https://github.com/huggingface/diffusers)

```py
from diffusers import AutoPipelineForText2Image
import torch

pipeline = AutoPipelineForText2Image.from_pretrained('black-forest-labs/FLUX.1-dev', torch_dtype=torch.float16).to('cuda')
pipeline.load_lora_weights('brenomendes/cordel-flux-lora', weight_name='lora.safetensors')
image = pipeline('your prompt').images[0]
```

For more details, including weighting, merging and fusing LoRAs, check the [documentation on loading LoRAs in diffusers](https://huggingface.co/docs/diffusers/main/en/using-diffusers/loading_adapters)
