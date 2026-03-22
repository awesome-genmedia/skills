---
name: vidu-q2-text-to-image
description: "Vidu Q2 | Text to Image. Generate images from text prompts with configurable aspect ratio. Triggers: text to image, vidu, image generation, t2i"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu Q2 | Text to Image

Generate images from text prompts using Vidu Q2 with configurable aspect ratio and reproducible results via seed control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q2-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "a cozy cabin in the woods during autumn, warm lighting",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the output image. enum: 16:9, 9:16, 1:1 |
| prompt | string | | Text prompt for image generation, max 1500 characters. |
| seed | integer | | Random seed for generation. |

## Examples

**Landscape image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q2-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "vast desert dunes at golden hour, dramatic shadows, photorealistic",
      "aspect_ratio": "16:9",
      "seed": 42
    }
  }'
```

**Square portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q2-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "close-up portrait of an elderly craftsman with weathered hands, studio lighting",
      "aspect_ratio": "1:1"
    }
  }'
```

## Related Models

- [Vidu Q2 | Reference to Image](../vidu-q2-reference-to-image/) - Generate images using reference images
- [Bytedance | Seedream | v4.5 | Text to Image](../bytedance-seedream-v4-5-text-to-image/) - Alternative text-to-image model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
