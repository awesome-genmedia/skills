---
name: imagen-4-fast
description: "Imagen 4 | Fast. Generate images quickly using Google Imagen 4 Fast. High-speed AI image generation from text prompts. Triggers: imagen 4, google imagen, imagen fast, fast image generation, google image generation, imagen 4 fast"
allowed-tools: Bash(curl *), WebFetch
---

# Imagen 4 | Fast

Generate images quickly using Google Imagen 4 Fast. A speed-optimized version of Google's Imagen 4 model for rapid text-to-image generation with configurable aspect ratios, output formats, and safety filters.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "imagen-4-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic red fox sitting in a snowy forest clearing, soft winter light filtering through pine trees",
      "aspect_ratio": "16:9",
      "output_format": "jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Image aspect ratio. Options: `1:1`, `9:16`, `16:9`, `3:4`, `4:3` |
| output_format | string | jpg | Output format. Options: `jpg`, `png` |
| prompt | string | - | Text prompt for image generation |
| safety_filter_level | string | block_only_high | Safety filter level. Options: `block_low_and_above`, `block_medium_and_above`, `block_only_high` |

## Examples

**Portrait image in PNG:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "imagen-4-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "Professional headshot of a confident business woman in a modern office, natural lighting, sharp focus",
      "aspect_ratio": "3:4",
      "output_format": "png"
    }
  }'
```

**Widescreen landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "imagen-4-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A vast savanna at golden hour, acacia trees silhouetted against a fiery sky, a herd of elephants walking in the distance",
      "aspect_ratio": "16:9",
      "output_format": "jpg",
      "safety_filter_level": "block_only_high"
    }
  }'
```

## Related Models

- [Qwen Image](../qwen-image/) - Qwen text-to-image
- [Seedream V3 | Text to Image](../seedream-v3-text-to-image/) - ByteDance text-to-image
- [Ideogram V3 | Turbo](../ideogram-v3-turbo/) - Ideogram with text rendering

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
