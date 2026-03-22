---
name: kling-v2-5-turbo-pro-image-to-video
description: "Kling v2.5 | Turbo | Pro | Image to Video. Animate images into videos with tail image support using Kling v2.5 Turbo Pro. Triggers: kling, image to video, kling pro, kling turbo, animate image"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v2.5 | Turbo | Pro | Image to Video

Animate images into videos using the Kling v2.5 Turbo Pro model. Supports start and end frame images (tail image), CFG scale for prompt adherence, and negative prompts for quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/hero-scene.jpg",
      "prompt": "The hero leaps into action, cape flowing behind them in slow motion",
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
| tail_image_url | string | | URL of the image to be used for the end of the video |

## Examples

**Start-to-end frame animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/door-closed.jpg",
      "tail_image_url": "https://example.com/door-open.jpg",
      "prompt": "The door slowly opens revealing a bright sunlit garden behind it",
      "duration": "5",
      "cfg_scale": 0.6
    }
  }'
```

**Extended product showcase:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-5-turbo-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/watch-front.jpg",
      "prompt": "Camera slowly rotates around the luxury watch, highlighting its craftsmanship",
      "duration": "10",
      "cfg_scale": 0.7,
      "negative_prompt": "blur, distort, low quality, shaky, artifacts"
    }
  }'
```

## Related Models

- [kling-v2-5-turbo-pro-text-to-video](../kling-v2-5-turbo-pro-text-to-video/) - Pro text to video
- [kling-v2-5-turbo-standard-image-to-video](../kling-v2-5-turbo-standard-image-to-video/) - Standard tier image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
