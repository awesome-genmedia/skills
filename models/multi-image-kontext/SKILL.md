---
name: multi-image-kontext
description: "Flux Multi Image Kontext. Combine and transform up to 4 images using Flux Kontext. Multi-image AI editing and composition. Triggers: flux multi image, multi image kontext, combine multiple images, flux kontext multi, multi image edit, image composition"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Multi Image Kontext

Combine and transform up to 4 images using Flux Kontext. The standard multi-image model supporting up to 4 input images with text-guided combination, style transfer, and transformation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/face.jpg",
      "input_image_2": "https://example.com/outfit.jpg",
      "prompt": "The person from image 1 wearing the outfit from image 2, professional fashion photo"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | match_input_image | Output aspect ratio. Options: `match_input_image`, `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `4:5`, `5:4`, `21:9`, `9:21`, `2:1`, `1:2` |
| input_image_1 | string | - | First input image. Must be jpeg, png, gif, or webp |
| input_image_2 | string | - | Second input image. Must be jpeg, png, gif, or webp |
| input_image_3 | string | - | Third input image (optional) |
| input_image_4 | string | - | Fourth input image (optional) |
| prompt | string | - | Text description of how to combine or transform the images |
| safety_tolerance | integer | 6 | Safety tolerance level |
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Combine person with background and style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/person.jpg",
      "input_image_2": "https://example.com/beach-bg.jpg",
      "input_image_3": "https://example.com/sunset-lighting.jpg",
      "prompt": "Place the person from image 1 on the beach from image 2 with the warm sunset lighting from image 3",
      "aspect_ratio": "16:9"
    }
  }'
```

**Multi-reference character design:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/face-ref.jpg",
      "input_image_2": "https://example.com/armor-ref.jpg",
      "input_image_3": "https://example.com/pose-ref.jpg",
      "input_image_4": "https://example.com/color-palette.jpg",
      "prompt": "Create a character with the face from image 1, wearing armor from image 2, in the pose from image 3, using the color palette from image 4",
      "aspect_ratio": "3:4",
      "seed": 42
    }
  }'
```

## Related Models

- [Flux Kontext | Max | Multi Image](../multi-image-kontext-max/) - Highest quality (2 images)
- [Flux Kontext | Pro | Multi Image](../multi-image-kontext-pro/) - Pro tier (2 images)
- [Flux.1 Kontext | Pro](../flux-kontext-pro/) - Single-image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
