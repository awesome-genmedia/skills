---
name: xai-grok-imagine-image-to-video
description: "XAI | Grok Imagine | Image to Video. Animate images into videos with configurable aspect ratio and duration. Triggers: image to video, grok, xai, animate, i2v"
allowed-tools: Bash(curl *), WebFetch
---

# XAI | Grok Imagine | Image to Video

Animate static images into videos using xAI's Grok Imagine with configurable aspect ratios, duration, and resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The flowers sway gently in the breeze as butterflies flutter around",
      "image_url": "https://example.com/garden.jpg",
      "duration": 5,
      "aspect_ratio": "16:9",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | auto | Aspect ratio. enum: 16:9, 4:3, 3:2, 1:1, 2:3, 3:4, 9:16 |
| duration | integer | 5 | Video duration in seconds. |
| image_url | string | | URL of the input image for video generation. |
| prompt | string | | Text description of desired changes or motion. |
| resolution | string | 720p | Output video resolution. enum: 480p, 720p |

## Examples

**Landscape animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Clouds move slowly across the sky as the sun casts long shadows over the valley",
      "image_url": "https://example.com/valley-sunset.jpg",
      "duration": 8,
      "aspect_ratio": "16:9",
      "resolution": "720p"
    }
  }'
```

**Portrait animation for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The person smiles and slightly tilts their head",
      "image_url": "https://example.com/selfie.jpg",
      "duration": 3,
      "aspect_ratio": "9:16"
    }
  }'
```

## Related Models

- [xai-grok-imagine-text-to-video](../xai-grok-imagine-text-to-video/) - Grok text to video
- [xai-grok-imagine-edit-video](../xai-grok-imagine-edit-video/) - Grok video editing
- [xai-grok-imagine-image-edit](../xai-grok-imagine-image-edit/) - Grok image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
