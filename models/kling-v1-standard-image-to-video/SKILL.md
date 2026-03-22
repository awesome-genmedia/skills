---
name: kling-v1-standard-image-to-video
description: "Kling v1 | Standard | Image to Video. Convert images to videos using Kling v1 Standard with masking and end-frame support. Affordable Kling image animation. Triggers: kling v1 standard image to video, kling standard i2v, kling v1 animate image, kling standard image animation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v1 | Standard | Image to Video

Convert images to videos using Kling v1 Standard. Features static masking for selective animation and end-frame targeting for controlled transitions, at an affordable price point.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Clouds moving across the sky, gentle wind blowing through the grass",
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
| negative_prompt | string | blur, distort, and low quality | Things to avoid |
| prompt | string | - | Text prompt for the animation |
| static_mask_url | string | - | URL of a mask image defining static (non-animated) areas |
| tail_image_url | string | - | URL of the image to use for the end of the video |

## Examples

**Image animation with end frame:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/closed-flower.jpg",
      "tail_image_url": "https://example.com/open-flower.jpg",
      "prompt": "The flower slowly opens its petals, time-lapse bloom",
      "aspect_ratio": "1:1",
      "duration": 5
    }
  }'
```

**Animation with static mask:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait-with-background.jpg",
      "static_mask_url": "https://example.com/person-mask.png",
      "prompt": "Background clouds moving, leaves blowing in wind, person stays still",
      "aspect_ratio": "9:16",
      "negative_prompt": "blur, distort, and low quality"
    }
  }'
```

## Related Models

- [Kling v1 | Pro | Image to Video](../kling-v1-pro-image-to-video/) - Higher quality Pro tier
- [Kling v2.1 | Standard | Image to Video](../kling-v2-1-standard-image-to-video/) - Latest generation
- [Kling v1 | Standard | Text to Video](../kling-v1-standard-text-to-video/) - Standard text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
