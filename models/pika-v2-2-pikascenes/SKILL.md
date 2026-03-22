---
name: pika-v2-2-pikascenes
description: "Pika | v2.2 | PikaScenes. Combine multiple images into videos with scene modes. Triggers: video generation, pika, scenes, multi-image, video composition"
allowed-tools: Bash(curl *), WebFetch
---

# Pika | v2.2 | PikaScenes

Combine multiple images into videos using PikaScenes. Supports precise and creative ingredient modes for blending images with text-guided video generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-pikascenes",
    "version": "0.0.1",
    "input": {
      "prompt": "two characters meeting at a park, gentle breeze",
      "image_urls": ["https://example.com/character1.jpg", "https://example.com/park-bg.jpg"],
      "duration": 5,
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 16:9, 9:16, 1:1, 4:5, 5:4, 3:2, 2:3 |
| duration | integer | 5 | The duration of the generated video in seconds. |
| image_urls | array | | URLs of images to combine into a video. |
| ingredients_mode | string | precise | Mode for integrating multiple images. enum: precise, creative |
| negative_prompt | string | ugly, bad, terrible | A negative prompt to guide the model. |
| prompt | string | | Text prompt describing the desired video. |
| resolution | string | 1080p | The resolution of the generated video. enum: 720p, 1080p |
| seed | integer | | The seed for the random number generator. |

## Examples

**Creative multi-image blend:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-pikascenes",
    "version": "0.0.1",
    "input": {
      "prompt": "magical transformation scene, sparkles and light effects",
      "image_urls": ["https://example.com/before.jpg", "https://example.com/after.jpg"],
      "ingredients_mode": "creative",
      "duration": 5,
      "resolution": "1080p",
      "aspect_ratio": "16:9"
    }
  }'
```

**Precise scene composition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-2-pikascenes",
    "version": "0.0.1",
    "input": {
      "prompt": "product being used in a kitchen, smooth camera pan",
      "image_urls": ["https://example.com/product.jpg", "https://example.com/kitchen.jpg"],
      "ingredients_mode": "precise",
      "duration": 5,
      "resolution": "1080p",
      "negative_prompt": "blurry, distorted, low quality",
      "seed": 42
    }
  }'
```

## Related Models

- [Pika | v2.2 | Image to Video](../pika-v2-2-image-to-video/) - Single image to video
- [Pika | v2.2 | Text to Video](../pika-v2-2-text-to-video/) - Text-only video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
