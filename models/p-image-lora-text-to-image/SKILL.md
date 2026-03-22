---
name: p-image-lora-text-to-image
description: "Pruna | P-Image LoRA | Text to Image. Generate images from text prompts using custom LoRA weights. Triggers: text to image, lora, pruna, generate image, t2i"
allowed-tools: Bash(curl *), WebFetch
---

# Pruna | P-Image LoRA | Text to Image

Generate images from text descriptions using custom LoRA weights from HuggingFace. Supports configurable aspect ratios, prompt upsampling, and custom dimensions.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-lora-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene mountain landscape at sunset with golden light",
      "lora_weights": "https://huggingface.co/my-org/my-style-lora",
      "lora_scale": 0.5,
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio for the generated image. custom: use width/height for exact dimensions. enum: 1:1, 16:9, 9:16, 4:3, 3:4, 3:2, 2:3, custom |
| disable_safety_checker | boolean | false | Disable safety checker for generated images. |
| height | integer | false | Custom height in pixels (256-1440, multiple of 16). Only when aspect_ratio=custom. |
| hf_api_token | string | false | HuggingFace API token for accessing private LoRA repositories. |
| lora_scale | number | 0.5 | LoRA strength (-1 to 3). 0.5 works well for most LoRAs. |
| lora_weights | string | false | HuggingFace URL to LoRA weights. |
| prompt | string | false | Text description of the image to generate. |
| prompt_upsampling | boolean | false | Upsample prompt with LLM for enhanced results. |
| seed | integer | false | Random seed for reproducible generation. |
| width | integer | false | Custom width in pixels (256-1440, multiple of 16). Only when aspect_ratio=custom. |

## Examples

**Generate a landscape image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-lora-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cyberpunk cityscape with neon lights reflecting on wet streets",
      "lora_weights": "https://huggingface.co/my-org/cyberpunk-lora",
      "aspect_ratio": "16:9",
      "prompt_upsampling": true
    }
  }'
```

**Custom dimensions with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-lora-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Portrait of a fantasy elf warrior in armor",
      "lora_weights": "https://huggingface.co/my-org/fantasy-lora",
      "lora_scale": 0.7,
      "aspect_ratio": "custom",
      "width": 768,
      "height": 1024,
      "seed": 12345
    }
  }'
```

**Square image with high LoRA influence:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-lora-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A still life painting of flowers in a vase",
      "lora_weights": "https://huggingface.co/my-org/oil-painting-lora",
      "lora_scale": 1.5,
      "aspect_ratio": "1:1"
    }
  }'
```

## Related Models

- [p-image-edit-lora-image-edit](../p-image-edit-lora-image-edit/) - Image editing with LoRA weights
- [p-image-text-to-image](../p-image-text-to-image/) - Standard text to image without LoRA
- [p-image-edit](../p-image-edit/) - Image editing without LoRA

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
