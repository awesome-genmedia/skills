---
name: wan-2-5-preview-image-to-video
description: "Wan | 2.5 | Preview | Image to Video. Animate images into videos with audio support using the Wan 2.5 Preview model. Triggers: wan, image to video, animate image, wan 2.5, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | 2.5 | Preview | Image to Video

Animate images into videos with optional background audio using the Wan 2.5 Preview model. Supports LLM-based prompt expansion, configurable duration, and multiple resolutions.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset-photo.jpg",
      "prompt": "The sun slowly dips below the horizon as colors shift from orange to purple",
      "duration": "5",
      "resolution": "720p",
      "enable_prompt_expansion": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | | URL of background music audio (must be publicly accessible) |
| duration | string | 5 | Duration of the generated video in seconds. enum: 5, 10 |
| enable_prompt_expansion | boolean | true | Whether to enable LLM-based prompt rewriting |
| image_url | string | | URL of the image to use as the first frame |
| negative_prompt | string | | Negative prompt to avoid (max 500 chars) |
| prompt | string | | Text prompt describing desired video motion (max 800 chars) |
| resolution | string | 720p | Video resolution. enum: 480p, 720p, 1080p |
| seed | integer | | Random seed for reproducibility |

## Examples

**1080p video with background music:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/city-night.jpg",
      "prompt": "Cars stream by with light trails, neon signs flicker, camera slowly pans right",
      "duration": "10",
      "resolution": "1080p",
      "audio_url": "https://example.com/ambient-city-sounds.mp3",
      "enable_prompt_expansion": true
    }
  }'
```

**Quick preview with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/flower-garden.jpg",
      "prompt": "Gentle breeze sways the flowers, butterflies flutter between petals",
      "duration": "5",
      "resolution": "480p",
      "negative_prompt": "blurry, jittery, low quality",
      "seed": 42
    }
  }'
```

## Related Models

- [wan-2-5-preview-text-to-video](../wan-2-5-preview-text-to-video/) - Text to video
- [wan-2-5-preview-text-to-image](../wan-2-5-preview-text-to-image/) - Text to image
- [wan-2-5-preview-image-to-image](../wan-2-5-preview-image-to-image/) - Image to image editing
- [wan-v2-2-14b-animate-move](../wan-v2-2-14b-animate-move/) - Motion transfer animation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
