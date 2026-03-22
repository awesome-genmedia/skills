---
name: flux-kontext-pro
description: "Flux.1 Kontext | Pro. Generate and edit images using Flux Kontext Pro. Professional AI image generation and editing. Triggers: flux kontext pro, kontext pro, flux pro, professional image edit, flux image generation, kontext pro edit"
allowed-tools: Bash(curl *), WebFetch
---

# Flux.1 Kontext | Pro

Generate and edit images using Flux Kontext Pro. Professional-grade image generation from text and image editing with reference images. A balanced option between speed and quality in the Flux Kontext family.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy bookstore interior with warm lamp light, stacked vintage books, and a tabby cat sleeping on a windowsill",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | match_input_image | Output aspect ratio. Options: `match_input_image`, `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `4:5`, `5:4`, `21:9`, `9:21`, `2:1`, `1:2` |
| input_image | string | - | Reference image. Must be jpeg, png, gif, or webp |
| prompt | string | - | Text description for generation or editing instruction |
| safety_tolerance | integer | 6 | Safety tolerance level |
| seed | integer | - | Random seed for reproducible generation (min: 1, max: 1000000000000000000) |

## Examples

**Generate from text:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "An isometric 3D render of a tiny pixel art village with a river, bridge, and windmill, soft pastel colors",
      "aspect_ratio": "1:1",
      "seed": 42
    }
  }'
```

**Edit an existing image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-pro",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/landscape.jpg",
      "prompt": "Add a hot air balloon floating in the sky and change the season to autumn with orange and red foliage",
      "aspect_ratio": "match_input_image"
    }
  }'
```

## Related Models

- [Flux.1 Kontext | Max](../flux-kontext-max/) - Highest quality tier
- [Flux Kontext | Pro | Multi Image](../multi-image-kontext-pro/) - Pro with multi-image support
- [Flux.1 Kontext Dev Lora](../flux-kontext-dev-lora/) - Custom LoRA support

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
