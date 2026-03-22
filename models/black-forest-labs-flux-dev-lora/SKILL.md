---
name: black-forest-labs-flux-dev-lora
description: "Black Forest Labs | Flux Dev Lora. Generate images with Flux Dev and LoRA weights from multiple sources. Triggers: text to image, flux dev, lora, bfl, image generation, civitai, huggingface"
allowed-tools: Bash(curl *), WebFetch
---

# Black Forest Labs | Flux Dev Lora

Generate images with Flux Dev model and custom LoRA weights from Replicate, HuggingFace, CivitAI, or direct URLs. Supports image-to-image mode and multiple output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "black-forest-labs-flux-dev-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "a serene lake at twilight with reflections, photorealistic",
      "lora_weights": "https://example.com/nature-lora.safetensors",
      "lora_scale": 0.8,
      "aspect_ratio": "16:9",
      "guidance": 3
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Aspect ratio of the output. enum: 1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21 |
| civitai_api_token | string | | CivitAI API token for authenticated LoRA downloads. |
| disable_safety_checker | boolean | false | Disable safety checker for generated images. |
| extra_lora | string | | Additional LoRA weights URL. Supports Replicate and HuggingFace formats. |
| extra_lora_scale | number | 1 | Scale for the extra LoRA (0-2). |
| go_fast | boolean | false | Run with fp8 quantized model for faster predictions. |
| guidance | number | 3 | Guidance scale for generated image. |
| hf_api_token | string | | HuggingFace API token for authenticated LoRA downloads. |
| image | string | | Input image for image-to-image mode. Output matches input aspect ratio. |
| lora_scale | number | 1 | Scale for the main LoRA (0-2). |
| lora_weights | string | | Main LoRA weights. Supports Replicate, HuggingFace, CivitAI, or URL. |
| megapixels | string | 1 | Output megapixels. enum: 1, 0.25 |
| num_inference_steps | integer | 28 | Number of denoising steps (28-50 recommended). |
| num_outputs | integer | 1 | Number of outputs to generate. |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 80 | Quality for output images (0-100). |
| prompt | string | | Prompt for generated image. |
| prompt_strength | number | 0.8 | Prompt strength for img2img mode (1.0 = full destruction). |
| seed | integer | | Random seed for reproducible generation. |

## Examples

**LoRA from HuggingFace:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "black-forest-labs-flux-dev-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "anime girl in a cherry blossom garden, detailed",
      "lora_weights": "username/anime-style-lora",
      "lora_scale": 0.9,
      "aspect_ratio": "3:4",
      "num_inference_steps": 30,
      "output_format": "png"
    }
  }'
```

**Image-to-image with dual LoRAs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "black-forest-labs-flux-dev-lora",
    "version": "0.0.1",
    "input": {
      "prompt": "vintage film photography style, warm tones",
      "image": "https://example.com/input-photo.jpg",
      "lora_weights": "https://example.com/vintage-lora.safetensors",
      "lora_scale": 0.7,
      "extra_lora": "https://example.com/film-grain-lora.safetensors",
      "extra_lora_scale": 0.5,
      "prompt_strength": 0.6,
      "seed": 42
    }
  }'
```

## Related Models

- [BFL Flux Lora](../bfl-flux-lora/) - BFL Flux with LoRA support
- [Flux 2 | Text to Image Lora](../flux-2-lora/) - Flux 2 with LoRA support

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
