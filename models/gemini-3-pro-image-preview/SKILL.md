---
name: gemini-3-pro-image-preview
description: "Gemini 3 | Pro | Image Preview. Generate images from text using Google Gemini with up to 4K resolution. Triggers: text to image, gemini, google, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Gemini 3 | Pro | Image Preview

Generate images from text prompts using Google's Gemini 3 Pro model. Supports multiple aspect ratios, resolution up to 4K, and batch generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gemini-3-pro-image-preview",
    "version": "0.0.1",
    "input": {
      "prompt": "a cozy reading nook by a window on a rainy day, warm lighting",
      "aspect_ratio": "4:3",
      "resolution": "1K"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | The aspect ratio of the generated image. enum: 21:9, 16:9, 3:2, 4:3, 5:4, 1:1, 4:5, 3:4, 2:3, 9:16 |
| num_images | integer | 1 | The number of images to generate. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The text prompt to generate an image from. |
| resolution | string | 1K | The resolution of the image to generate. enum: 1K, 2K, 4K |

## Examples

**Ultra-wide cinematic shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gemini-3-pro-image-preview",
    "version": "0.0.1",
    "input": {
      "prompt": "epic sci-fi space station orbiting a gas giant, cinematic lighting",
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
    "model": "gemini-3-pro-image-preview",
    "version": "0.0.1",
    "input": {
      "prompt": "watercolor portrait of an old fisherman, weathered face, kind eyes",
      "aspect_ratio": "3:4",
      "resolution": "2K",
      "num_images": 4,
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [Gemini 3 Pro | Image Edit](../gemini-3-pro-image-preview-edit/) - Image editing with Gemini
- [Nano Banana Pro](../nano-banana-pro/) - Alternative text-to-image model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
