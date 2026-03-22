---
name: kling-v2-1-standard-image-to-video
description: "Kling v2.1 | Standard | Image to Video. Convert images to videos using Kling v2.1 Standard. Fast and affordable Kling image-to-video. Triggers: kling standard image to video, kling v2.1 standard, kling standard animate, kling standard i2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2.1 | Standard | Image to Video

Convert images to videos using Kling v2.1 Standard. The most affordable tier for Kling v2.1 image-to-video generation, offering good quality with fast processing and control over aspect ratio, duration, and CFG scale.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/park-bench.jpg",
      "prompt": "Leaves falling from trees, a bird landing on the bench, gentle autumn breeze",
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. Options: `16:9`, `9:16`, `1:1` |
| cfg_scale | number | 0.5 | Classifier-free guidance scale |
| duration | integer | 5 | Video duration in seconds |
| image_url | string | - | URL of the input image |
| negative_prompt | string | - | Text describing what to avoid |
| prompt | string | - | Text prompt to guide the animation |

## Examples

**Quick landscape animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/river.jpg",
      "prompt": "Water flowing over rocks, ripples and splashes, sunlight sparkling on the surface",
      "aspect_ratio": "16:9",
      "negative_prompt": "blurry, distorted"
    }
  }'
```

**Square format for social:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/food-plate.jpg",
      "prompt": "Steam rising from the hot dish, sauce slowly drizzling, appetizing food presentation",
      "aspect_ratio": "1:1",
      "duration": 5
    }
  }'
```

## Related Models

- [Kling v2.1 | Master | Image to Video](../kling-v2-1-master-image-to-video/) - Highest quality tier
- [Kling v2.1 | Pro | Image to Video](../kling-v2-1-pro-image-to-video/) - Pro tier with end-frame support
- [Kling v1 | Standard | Image to Video](../kling-v1-standard-image-to-video/) - Previous generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
