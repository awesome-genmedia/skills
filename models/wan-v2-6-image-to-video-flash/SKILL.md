---
name: wan-v2-6-image-to-video-flash
description: "Wan | v2.6 | Image to Video | Flash. Fast image-to-video generation with audio support, multi-shot, and up to 1080p. Triggers: image to video, wan, flash, animate, i2v, video"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.6 | Image to Video | Flash

Fast image-to-video generation using Wan v2.6 Flash with prompt expansion, audio background, multi-shot segmentation, and up to 1080p resolution. Generate videos up to 15 seconds.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-video-flash",
    "version": "0.0.1",
    "input": {
      "prompt": "The ocean waves crash dramatically against the rocky shore as seabirds fly overhead",
      "image_url": "https://example.com/coastal-scene.jpg",
      "duration": "10",
      "resolution": "1080p",
      "enable_prompt_expansion": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | | URL of background audio. Must be publicly accessible. |
| duration | string | 15 | Duration in seconds. enum: 5, 10, 15 |
| enable_prompt_expansion | boolean | true | Enable prompt rewriting using LLM. |
| enable_safety_checker | boolean | true | Enable safety checker for generated content. |
| image_url | string | | URL of the image for the first frame. Must be publicly accessible or base64. |
| multi_shots | boolean | false | Enable intelligent multi-shot segmentation. Only active with prompt expansion. |
| negative_prompt | string | | Negative prompt to describe content to avoid. Max 500 characters. |
| prompt | string | | Text prompt describing desired video motion. Max 800 characters. |
| resolution | string | 1080p | Video resolution. enum: 720p, 1080p |
| seed | integer | | Random seed for reproducibility. |

## Examples

**High-res animation with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-video-flash",
    "version": "0.0.1",
    "input": {
      "prompt": "The forest comes alive with fireflies flickering in the twilight",
      "image_url": "https://example.com/forest-dusk.jpg",
      "audio_url": "https://example.com/nature-ambient.mp3",
      "duration": "15",
      "resolution": "1080p"
    }
  }'
```

**Quick animation with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-video-flash",
    "version": "0.0.1",
    "input": {
      "prompt": "A cat slowly opens its eyes and stretches lazily",
      "image_url": "https://example.com/sleeping-cat.jpg",
      "duration": "5",
      "resolution": "720p",
      "negative_prompt": "blurry, distorted, jittery motion",
      "seed": 42
    }
  }'
```

**Multi-shot video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-video-flash",
    "version": "0.0.1",
    "input": {
      "prompt": "A sweeping camera movement reveals the grand architecture of an ancient temple, then zooms into intricate carvings",
      "image_url": "https://example.com/temple.jpg",
      "duration": "15",
      "multi_shots": true,
      "enable_prompt_expansion": true
    }
  }'
```

## Related Models

- [pixverse-v5-6-image-to-video](../pixverse-v5-6-image-to-video/) - Pixverse image to video
- [kling-v3-standard-image-to-video](../kling-v3-standard-image-to-video/) - Kling v3 image to video
- [xai-grok-imagine-image-to-video](../xai-grok-imagine-image-to-video/) - Grok image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
