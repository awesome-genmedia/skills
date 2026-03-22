---
name: multi-image-kontext-pro
description: "Flux Kontext | Pro | Multi Image. Combine and transform multiple images using Flux Kontext Pro. Professional multi-image AI editing. Triggers: flux kontext pro multi, multi image kontext pro, combine images pro, flux pro multi image, kontext pro edit"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Kontext | Pro | Multi Image

Combine and transform multiple images using Flux Kontext Pro. Professional-grade multi-image operations with two input images, text-guided combination, and high-quality output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext-pro",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/product.jpg",
      "input_image_2": "https://example.com/background.jpg",
      "prompt": "Place the product from the first image onto the background from the second image with soft studio lighting"
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

**Merge outfit onto person:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext-pro",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/model.jpg",
      "input_image_2": "https://example.com/dress.jpg",
      "prompt": "Put the outfit from the second image on the person in the first image, natural pose, professional fashion photography",
      "aspect_ratio": "3:4",
      "output_format": "png"
    }
  }'
```

**Combine elements from two scenes:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "multi-image-kontext-pro",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/car.jpg",
      "input_image_2": "https://example.com/mountain-road.jpg",
      "prompt": "The car from image one driving on the mountain road from image two, cinematic shot",
      "aspect_ratio": "16:9",
      "seed": 7890
    }
  }'
```

## Related Models

- [Flux Kontext | Max | Multi Image](../multi-image-kontext-max/) - Highest quality multi-image
- [Flux Multi Image Kontext](../multi-image-kontext/) - Standard multi-image (up to 4 images)
- [Flux.1 Kontext | Pro](../flux-kontext-pro/) - Single-image Kontext Pro

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
