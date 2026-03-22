---
name: sora-2-image-to-video-pro
description: "Sora 2 | Image to Video | Pro. Animate images into high-quality videos using OpenAI Sora 2 Pro. Triggers: sora, image to video, sora 2, sora pro, animate image, openai sora"
allowed-tools: Bash(curl *), WebFetch
---

# Sora 2 | Image to Video | Pro

Animate images into high-quality videos using OpenAI Sora 2 Pro. Supports configurable duration, aspect ratio, and resolution up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-image-to-video-pro",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset-beach.jpg",
      "prompt": "Waves gently lap at the shore as the sun slowly sets, colors shifting across the sky",
      "duration": 4,
      "aspect_ratio": "16:9",
      "resolution": "1080p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| duration | integer | 4 | Duration of the generated video in seconds |
| image_url | string | | The URL of the image to use as the first frame |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | The resolution of the generated video. enum: 720p, 1080p |

## Examples

**1080p cinematic animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-image-to-video-pro",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/city-skyline.jpg",
      "prompt": "Traffic flows through the city streets below, lights flickering, time-lapse feel",
      "duration": 4,
      "resolution": "1080p",
      "aspect_ratio": "16:9"
    }
  }'
```

**Vertical portrait animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sora-2-image-to-video-pro",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/fashion-model.jpg",
      "prompt": "Model turns slowly on the runway, fabric flowing with each step",
      "duration": 4,
      "aspect_ratio": "9:16",
      "resolution": "720p"
    }
  }'
```

## Related Models

- [sora-2-text-to-video-pro](../sora-2-text-to-video-pro/) - Pro text to video
- [sora-2-image-to-video](../sora-2-image-to-video/) - Standard image to video
- [sora-2-text-to-video](../sora-2-text-to-video/) - Standard text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
