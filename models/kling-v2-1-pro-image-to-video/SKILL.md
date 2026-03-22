---
name: kling-v2-1-pro-image-to-video
description: "Kling v2.1 | Pro | Image to Video. Convert images to videos using Kling v2.1 Pro with end-frame targeting. Professional Kling image-to-video. Triggers: kling pro image to video, kling v2.1 pro i2v, kling pro animate, kling pro video"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2.1 | Pro | Image to Video

Convert images to videos using Kling v2.1 Pro. Professional-grade image-to-video generation with support for end-frame targeting via tail_image_url, CFG scale control, and negative prompting.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/garden.jpg",
      "prompt": "Flowers swaying in a gentle breeze, butterflies fluttering around",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| cfg_scale | number | 0.5 | Classifier-free guidance scale |
| duration | integer | 5 | Video duration in seconds |
| image_url | string | - | URL of the input image |
| negative_prompt | string | - | Text describing what to avoid |
| prompt | string | - | Text prompt to guide the animation |
| tail_image_url | string | - | URL of the image to use for the end of the video |

## Examples

**Animate with end frame transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunrise.jpg",
      "tail_image_url": "https://example.com/sunset.jpg",
      "prompt": "Smooth transition from sunrise to sunset, clouds moving across the sky, changing light",
      "duration": 5
    }
  }'
```

**Simple image animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/street-scene.jpg",
      "prompt": "People walking, cars passing by, dynamic urban life",
      "cfg_scale": 0.5,
      "negative_prompt": "blurry, distorted, low quality"
    }
  }'
```

## Related Models

- [Kling v2.1 | Master | Image to Video](../kling-v2-1-master-image-to-video/) - Higher quality Master tier
- [Kling v2.1 | Standard | Image to Video](../kling-v2-1-standard-image-to-video/) - Standard tier
- [Kling v1 | Pro | Image to Video](../kling-v1-pro-image-to-video/) - Previous generation Pro

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
