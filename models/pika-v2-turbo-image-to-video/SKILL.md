---
name: pika-v2-turbo-image-to-video
description: "Pika | v2 | Turbo | Image to Video. Fast image-to-video generation with Pika Turbo. Triggers: image to video, pika, turbo, fast, animation"
allowed-tools: Bash(curl *), WebFetch
---

# Pika | v2 | Turbo | Image to Video

Quickly animate images into videos using Pika v2 Turbo mode. Optimized for speed while maintaining quality output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-turbo-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-shot.jpg",
      "prompt": "camera orbits around the product, studio lighting",
      "duration": 5,
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | integer | 5 | The duration of the generated video in seconds. |
| image_url | string | | URL of the image to use as the first frame. |
| negative_prompt | string | | A negative prompt to guide the model. |
| prompt | string | | Text prompt describing the desired motion. |
| resolution | string | 720p | The resolution of the generated video. enum: 720p, 1080p |
| seed | integer | | The seed for the random number generator. |

## Examples

**Product animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-turbo-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sneaker.jpg",
      "prompt": "shoe rotating on a pedestal, spotlight effect",
      "duration": 5,
      "resolution": "1080p",
      "negative_prompt": "blurry, flickering"
    }
  }'
```

**Nature animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pika-v2-turbo-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cherry-blossom.jpg",
      "prompt": "petals gently falling, soft breeze",
      "duration": 5,
      "resolution": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [Pika | v2 | Turbo | Text to Video](../pika-v2-turbo-text-to-video/) - Turbo text-to-video
- [Pika | v2.2 | Image to Video](../pika-v2-2-image-to-video/) - Higher quality image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
