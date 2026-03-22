---
name: flux-kontext-max
description: "Flux.1 Kontext | Max. Generate and edit images using Flux Kontext Max. The highest quality tier for AI image generation and editing. Triggers: flux kontext max, kontext max, flux max, highest quality image edit, premium image generation, flux kontext"
allowed-tools: Bash(curl *), WebFetch
---

# Flux.1 Kontext | Max

Generate and edit images using Flux Kontext Max. The highest quality tier of the Flux Kontext family, offering premium image generation from text and image editing with reference images. Supports a wide range of aspect ratios.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-max",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic portrait of a woman with flowing red hair in a field of sunflowers, golden hour lighting, shallow depth of field",
      "aspect_ratio": "3:4"
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
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Text-to-image generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-max",
    "version": "0.0.1",
    "input": {
      "prompt": "A steampunk clockwork owl perched on an antique telescope, intricate brass gears and copper pipes, moody Victorian lighting",
      "aspect_ratio": "1:1",
      "seed": 42
    }
  }'
```

**Image editing with reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-kontext-max",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/room-photo.jpg",
      "prompt": "Change the wall color to a deep navy blue and add modern art paintings on the wall",
      "aspect_ratio": "match_input_image"
    }
  }'
```

## Related Models

- [Flux.1 Kontext | Pro](../flux-kontext-pro/) - Pro tier (faster, slightly lower quality)
- [Flux Kontext | Max | Multi Image](../multi-image-kontext-max/) - Max tier with multi-image support
- [Flux.1 Kontext Dev Lora](../flux-kontext-dev-lora/) - Custom LoRA support

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
