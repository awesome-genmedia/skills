---
name: flux-2-max-edit
description: "Flux 2 | Max | Edit. Edit images with the highest quality Flux 2 Max model. Triggers: image editing, flux max edit, high quality edit, ai modify image"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Max | Edit

Edit images using the highest quality Flux 2 Max model. Features configurable safety tolerance levels for content filtering and supports multiple input images for complex editing tasks.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-max-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform the building exterior to have art deco architectural details",
      "image_urls": ["https://example.com/building.jpg"],
      "image_size": "square_hd",
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| image_size | string | square_hd | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_urls | array | - | List of URLs of input images for editing. |
| output_format | string | jpeg | The format of the generated image. Options: `jpeg`, `png` |
| prompt | string | - | The prompt to generate an image from. |
| safety_tolerance | string | 2 | The safety tolerance level. 1 is most strict, 5 is most permissive. Options: `1`, `2`, `3`, `4`, `5` |
| seed | integer | - | The seed to use for the generation. |

## Examples

**Basic high-quality edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-max-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Replace the plain wall with a beautiful mural of a forest scene",
      "image_urls": ["https://example.com/room.jpg"]
    }
  }'
```

**Detailed edit with specific settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-max-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Age the photograph to look like it was taken in the 1920s with sepia tones and film grain",
      "image_urls": ["https://example.com/modern-portrait.jpg"],
      "image_size": "portrait_4_3",
      "output_format": "png",
      "safety_tolerance": "3",
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Max | Text to Image](../flux-2-max-text-to-image/) - Generate images from text with Flux 2 Max
- [Flux 2 | Turbo | Edit](../flux-2-turbo-edit/) - Faster editing with Flux 2 Turbo
- [Flux 2 | Flash | Edit](../flux-2-flash-edit/) - Ultra-fast editing with Flux 2 Flash

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
