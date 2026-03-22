---
name: nano-banana-pro
description: "Nano Banana Pro. Generate images from text with up to 4K resolution and multiple aspect ratios. Triggers: text to image, nano banana, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Nano Banana Pro

Generate images from text prompts with Nano Banana Pro. Supports a wide range of aspect ratios, up to 4K resolution, and batch generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a futuristic city with flying cars and neon signs, cyberpunk",
      "aspect_ratio": "16:9",
      "resolution": "1K"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | The aspect ratio of the generated image. enum: 21:9, 16:9, 3:2, 4:3, 5:4, 1:1, 4:5, 3:4, 2:3, 9:16 |
| limit_generations | boolean | false | Experimental parameter to limit the number of generations per round. |
| num_images | integer | 1 | The number of images to generate. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The text prompt to generate an image from. |
| resolution | string | 1K | The resolution of the image to generate. enum: 1K, 2K, 4K |

## Examples

**4K landscape generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "dramatic volcanic eruption at night, lava flows, stars visible, ultra detailed",
      "aspect_ratio": "21:9",
      "resolution": "4K",
      "output_format": "png"
    }
  }'
```

**Batch portrait generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "renaissance oil painting of a young scholar, rich warm tones",
      "aspect_ratio": "3:4",
      "resolution": "2K",
      "num_images": 4,
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [Nano Banana Pro | Edit](../nano-banana-pro-edit/) - Image editing variant
- [Gemini 3 | Pro | Image Preview](../gemini-3-pro-image-preview/) - Alternative text-to-image model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
