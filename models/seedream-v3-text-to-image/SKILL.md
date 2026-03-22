---
name: seedream-v3-text-to-image
description: "Seedream V3 | Text to Image. Generate images from text prompts using ByteDance Seedream V3. High-quality AI image generation with batch support. Triggers: seedream image, seedream v3, bytedance image, text to image seedream, seedream generate image, ai image seedream"
allowed-tools: Bash(curl *), WebFetch
---

# Seedream V3 | Text to Image

Generate images from text prompts using ByteDance Seedream V3. Create high-quality images with control over aspect ratio, guidance scale, and batch generation of multiple images at once.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedream-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A futuristic floating city above the clouds, connected by glass bridges, warm sunset lighting",
      "aspect_ratio": "16:9",
      "num_images": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Image aspect ratio. Options: `1:1`, `3:4`, `4:3`, `16:9`, `9:16`, `2:3`, `3:2`, `21:9` |
| guidance_scale | number | 2.5 | Controls alignment with the prompt. Higher values follow the prompt more closely |
| num_images | integer | 1 | Number of images to generate |
| prompt | string | - | Text prompt for image generation |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Generate a detailed illustration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedream-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "An enchanted library with floating books, magical glowing orbs, ancient wooden shelves reaching to the ceiling, fantasy art, highly detailed",
      "aspect_ratio": "3:4",
      "guidance_scale": 3.0,
      "seed": 12345
    }
  }'
```

**Batch generation of variations:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedream-v3-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A minimalist logo design of a mountain and sun, clean vector art, professional",
      "aspect_ratio": "1:1",
      "num_images": 4,
      "guidance_scale": 2.5
    }
  }'
```

## Related Models

- [Qwen Image](../qwen-image/) - Qwen text-to-image generation
- [Imagen 4 | Fast](../imagen-4-fast/) - Google's fast image generation
- [Ideogram V3 | Turbo](../ideogram-v3-turbo/) - Ideogram with text rendering

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
