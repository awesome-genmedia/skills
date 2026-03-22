---
name: bytedance-seedream-v4-5-text-to-image
description: "Bytedance | Seedream | v4.5 | Text to Image. Generate images from text prompts with Bytedance Seedream. Triggers: text to image, seedream, bytedance, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Bytedance | Seedream | v4.5 | Text to Image

Generate images from text prompts using Bytedance's Seedream v4.5 model. Supports multiple resolutions up to 4K and multi-image generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v4-5-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "a serene Japanese garden with cherry blossoms, photorealistic",
      "image_size": "landscape_4_3",
      "num_images": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_size | string | square_hd | Output image size. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9, auto_2K, auto_4K |
| max_images | integer | 1 | If set to a number greater than one, enables multi-image generation. |
| num_images | integer | 1 | Number of separate model generations to be run with the prompt. |
| prompt | string | | The text prompt used to generate the image. |
| seed | integer | | Random seed to control the stochasticity of image generation. |

## Examples

**High-resolution landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v4-5-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "dramatic mountain range at sunrise, volumetric lighting, 8K quality",
      "image_size": "auto_4K",
      "seed": 12345
    }
  }'
```

**Multiple portrait generations:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v4-5-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "oil painting portrait of a medieval knight, richly detailed armor",
      "image_size": "portrait_4_3",
      "num_images": 3
    }
  }'
```

## Related Models

- [Bytedance | Seedream | v4.5 | Edit](../bytedance-seedream-v4-5-edit/) - Edit existing images
- [Flux 2](../flux-2/) - Alternative text-to-image model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
