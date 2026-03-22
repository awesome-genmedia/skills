---
name: kling-v2-5-turbo-standard-image-to-video
description: "Kling v2.5 | Turbo | Standard | Image to Video. Animate images into videos using Kling v2.5 Turbo Standard model. Triggers: kling, image to video, animate image, kling turbo, kling standard"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2.5 | Turbo | Standard | Image to Video

Animate images into videos using the Kling v2.5 Turbo Standard model. Supports CFG scale for prompt adherence, configurable duration, and negative prompts for quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/car-on-road.jpg",
      "prompt": "The car drives forward along the winding mountain road with dust trailing behind",
      "duration": "5",
      "cfg_scale": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| cfg_scale | number | 0.5 | CFG (Classifier Free Guidance) scale for prompt adherence |
| duration | string | 5 | The duration of the generated video in seconds. enum: 5, 10 |
| image_url | string | | URL of the image to be used for the video |
| negative_prompt | string | blur, distort, and low quality | Negative prompt to avoid unwanted content |
| prompt | string | | Text prompt describing the desired video motion |

## Examples

**Short product animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-shoe.jpg",
      "prompt": "Camera slowly rotates around the shoe showcasing its design from every angle",
      "duration": "5",
      "cfg_scale": 0.7,
      "negative_prompt": "blur, distort, low quality, shaky"
    }
  }'
```

**Extended scene animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/garden-scene.jpg",
      "prompt": "Flowers sway in the breeze, a butterfly lands on a petal, soft natural movement",
      "duration": "10",
      "cfg_scale": 0.5
    }
  }'
```

## Related Models

- [kling-v2-5-turbo-pro-image-to-video](../kling-v2-5-turbo-pro-image-to-video/) - Pro tier image to video with tail image support
- [kling-v2-5-turbo-pro-text-to-video](../kling-v2-5-turbo-pro-text-to-video/) - Pro tier text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
