---
name: flux-hf-lora
description: "FLUX HF LoRA. Generate images using LoRA models with FLUX HF LoRA. Triggers: flux, image generation, lora"
allowed-tools: Bash(curl *), WebFetch
---

# FLUX HF LoRA

Generate images using LoRA models with FLUX HF LoRA. Supports multiple aspect ratios (1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21), reproducible results via seed.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-hf-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic portrait of a woman in a garden",
      "hf_lora": "alvdansen/frosting_lane_flux"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 1:1 | An enumeration.. Options: `1:1`, `16:9`, `21:9`, `3:2`, `2:3`, `4:5`, `5:4`, `3:4`, `4:3`, `9:16`, `9:21` |
| `disable_safety_checker` | boolean | True | Disable safety checker for generated images. This feature is only available thro |
| `guidance_scale` | number | 3.5 | Guidance scale for the diffusion process |
| `hf_lora` | string |  | HF, Replicate, CivitAI, or URL to a LoRA. Ex: alvdansen/frosting_lane_flux |
| `image` | string |  | Input image for image to image mode. The aspect ratio of your output will match |
| `lora_scale` | number | 0.8 | Scale for the LoRA weights |
| `num_inference_steps` | integer | 28 | Number of inference steps |
| `num_outputs` | integer | 1 | Number of images to output. |
| `output_format` | string | webp | An enumeration.. Options: `webp`, `jpg`, `png` |
| `output_quality` | integer | 80 | Quality when saving the output images, from 0 to 100. 100 is best quality, 0 is |
| `prompt` | string |  | Prompt for generated image |
| `prompt_strength` | number | 0.8 | Prompt strength (or denoising strength) when using image to image. 1.0 correspon |
| `seed` | integer |  | Random seed. Set for reproducible generation |

## Examples

**Generate with LoRA:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-hf-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic portrait of a woman in a garden",
      "hf_lora": "alvdansen/frosting_lane_flux"
    }
  }'
```

**LoRA with custom settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-hf-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "A fantasy landscape with crystalline structures",
      "hf_lora": "example/fantasy-lora",
      "lora_scale": 0.8,
      "guidance_scale": 4.0,
      "seed": 42
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
