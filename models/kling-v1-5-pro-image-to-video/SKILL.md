---
name: kling-v1-5-pro-image-to-video
description: "Kling v1.5 | Pro | Image to Video. Generate videos from images using Kling v1.5 | Pro | Image to Video. Triggers: image to video, kling, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v1.5 | Pro | Image to Video

Generate videos from images using Kling v1.5 | Pro | Image to Video. Supports multiple aspect ratios (16:9, 9:16, 1:1), configurable duration, negative prompt support, adjustable CFG scale.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Slow camera pan with gentle wind movement",
      "image_url": "https://example.com/your-image.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | The aspect ratio of the generated video frame. Options: `16:9`, `9:16`, `1:1` |
| `cfg_scale` | number | 0.5 | The CFG (Classifier Free Guidance) scale is a measure of how close you want the |
| `duration` | string | 5 | The duration of the generated video in seconds. Options: `5`, `10` |
| `image_url` | string |  | Image |
| `negative_prompt` | string | blur, distort, and low quality | Negative Prompt |
| `prompt` | string |  | Prompt |
| `tail_image_url` | string |  | URL of the image to be used for the end of the video |

## Examples

**Animate an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Slow camera pan with gentle wind movement",
      "image_url": "https://example.com/your-image.jpg"
    }
  }'
```

**Dynamic animation with controls:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-5-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Dynamic camera zoom with dramatic lighting changes",
      "image_url": "https://example.com/your-image.jpg",
      "aspect_ratio": "9:16",
      "duration": "10",
      "negative_prompt": "blurry, distorted, low quality, watermark",
      "cfg_scale": 0.7
    }
  }'
```

## Related Models

- [Kling v1.6 | Pro | Elements](../kling-v1-6-pro-elements/) - Generate creative element-based videos using Kling v1.6 | Pro | Elements.
- [Kling v1.6 | Standard | Elements](../kling-v1-6-standard-elements/) - Generate creative element-based videos using Kling v1.6 | Standard | Elements.
- [Kling v1.6 | Standard | Effects](../kling-v1-6-standart-effects/) - Apply visual effects to images and generate videos using Kling v1.6 | Standard | Effects.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
