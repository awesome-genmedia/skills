---
name: minimax-hailuo-v2-standard-image-to-video
description: "Minimax Hailuo V2 | Standard | Image to Video. Convert images to videos using Minimax Hailuo V2 Standard. Animate still images into dynamic video content. Triggers: hailuo image to video, minimax i2v, hailuo v2 standard, minimax image to video, animate image hailuo"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2 | Standard | Image to Video

Convert images to videos using Minimax Hailuo V2 Standard. Provide an image and a text prompt to generate a dynamic video with configurable duration, resolution, and prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/city-street.jpg",
      "prompt": "Cars driving past, people walking on the sidewalk, camera slowly panning right",
      "duration": 6
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | integer | 6 | Video duration in seconds. 10-second videos are not supported for some resolutions |
| image_url | string | - | URL of the input image |
| prompt | string | - | Text prompt to guide the animation |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer |
| resolution | string | 768P | Output resolution. Options: `768P`, `512P` |

## Examples

**Animate a landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset-beach.jpg",
      "prompt": "Waves gently rolling onto the shore, sun setting, warm golden light reflecting on the water",
      "duration": 6,
      "resolution": "768P"
    }
  }'
```

**Quick animation without prompt optimization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/flower-garden.jpg",
      "prompt": "Butterflies fluttering around the flowers, gentle breeze",
      "prompt_optimizer": false,
      "resolution": "512P"
    }
  }'
```

## Related Models

- [Minimax Hailuo V2 | Pro | Image to Video](../minimax-hailuo-v2-pro-image-to-video/) - Higher quality Pro variant
- [Minimax Hailuo V2 | Standard | Text to Video](../minimax-hailuo-v2-standard-text-to-video/) - Text-to-video standard
- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Google's image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
