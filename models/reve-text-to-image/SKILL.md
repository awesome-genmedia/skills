---
name: reve-text-to-image
description: "Reve | Text to Image. Generate images from text prompts using the Reve model. Triggers: reve, text to image, image generation, reve image"
allowed-tools: Bash(curl *), WebFetch
---

# Reve | Text to Image

Generate high-quality images from text descriptions using the Reve model. Supports multiple aspect ratios, output formats, and batch image generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A futuristic city skyline at twilight with flying cars and holographic billboards",
      "aspect_ratio": "16:9",
      "num_images": 1,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The desired aspect ratio. enum: 16:9, 9:16, 3:2, 2:3, 4:3, 3:4, 1:1 |
| num_images | integer | 1 | Number of images to generate |
| output_format | string | png | Output format. enum: png, jpeg, webp |
| prompt | string | | The text description of the desired image |

## Examples

**Portrait image for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Professional headshot of a confident businesswoman in a modern glass office, natural lighting",
      "aspect_ratio": "9:16",
      "num_images": 1,
      "output_format": "jpeg"
    }
  }'
```

**Multiple variations of a concept:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A magical forest with glowing mushrooms and fireflies, fantasy art style, ultra detailed",
      "aspect_ratio": "3:2",
      "num_images": 4,
      "output_format": "png"
    }
  }'
```

## Related Models

- [reve-edit](../reve-edit/) - Edit existing images with Reve
- [reve-remix](../reve-remix/) - Remix reference images with Reve

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
