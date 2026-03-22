---
name: cartoonify-v2
description: "Cartoonify V2. Convert photos to cartoon art style using AI. Transform any image into a high-quality cartoon illustration. Triggers: cartoonify, cartoon filter, photo to cartoon, cartoon style, image to cartoon, cartoon effect, ai cartoon"
allowed-tools: Bash(curl *), WebFetch
---

# Cartoonify V2

Convert photos into cartoon art style using AI. Transform any image into a stylized cartoon illustration with control over aspect ratio, output format, and safety settings.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "cartoonify-v2",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/portrait-photo.jpg",
      "aspect_ratio": "1:1",
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. Options: `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `4:5`, `5:4`, `21:9`, `9:21`, `2:1`, `1:2` |
| input_image | string | - | Image to convert to cartoon art style. Must be jpeg, png, or webp |
| output_format | string | png | Output format. Options: `jpg`, `png` |
| safety_tolerance | integer | 2 | Safety tolerance, 0 is most strict and 2 is most permissive |
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Cartoonify a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "cartoonify-v2",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/headshot.jpg",
      "aspect_ratio": "3:4",
      "output_format": "png",
      "seed": 12345
    }
  }'
```

**Cartoonify a landscape photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "cartoonify-v2",
    "version": "0.0.1",
    "input": {
      "input_image": "https://example.com/mountain-view.jpg",
      "aspect_ratio": "16:9",
      "output_format": "jpg"
    }
  }'
```

## Related Models

- [Hairstyle Changer](../change-haircut/) - Change hairstyles in photos
- [Pika v1.5 | Effects](../pika-v-1-5-effects/) - Apply creative effects to images
- [Flux.1 Kontext | Pro](../flux-kontext-pro/) - AI image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
