---
name: multi-image-kontext-max
description: "Flux Kontext | Max | Multi Image. Combine and transform multiple images using Flux Kontext Max. Highest quality multi-image AI editing. Triggers: flux kontext max multi, multi image kontext max, combine images max, flux max multi image, kontext max edit"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Kontext | Max | Multi Image

Combine and transform multiple images using Flux Kontext Max. The highest quality tier for multi-image operations, supporting two input images with text-guided combination, style transfer, and transformation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext-max",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/person.jpg",
      "input_image_2": "https://example.com/landscape.jpg",
      "prompt": "Place the person from the first image into the landscape from the second image, natural lighting, seamless blend",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | match_input_image | Output aspect ratio. Options: `match_input_image`, `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `4:5`, `5:4`, `21:9`, `9:21`, `2:1`, `1:2` |
| input_image_1 | string | - | First input image. Must be jpeg, png, gif, or webp |
| input_image_2 | string | - | Second input image. Must be jpeg, png, gif, or webp |
| output_format | string | png | Output format. Options: `jpg`, `png` |
| prompt | string | - | Text description of how to combine or transform the images |
| safety_tolerance | integer | 2 | Safety tolerance, 0 is most strict and 2 is most permissive |
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Combine person with new background:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext-max",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/headshot.jpg",
      "input_image_2": "https://example.com/office-bg.jpg",
      "prompt": "Place the person from the first image in the office setting from the second image, professional look",
      "output_format": "png",
      "seed": 42
    }
  }'
```

**Style transfer between images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext-max",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/photo.jpg",
      "input_image_2": "https://example.com/painting-style.jpg",
      "prompt": "Apply the artistic style from the second image to the content of the first image",
      "aspect_ratio": "1:1"
    }
  }'
```

## Related Models

- [Flux Kontext | Pro | Multi Image](../multi-image-kontext-pro/) - Pro tier multi-image
- [Flux Multi Image Kontext](../multi-image-kontext/) - Standard multi-image (up to 4 images)
- [Flux.1 Kontext | Max](../flux-kontext-max/) - Single-image Kontext Max

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
