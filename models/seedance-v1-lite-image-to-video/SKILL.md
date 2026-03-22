---
name: seedance-v1-lite-image-to-video
description: "Seedance V1 | Lite | Image to Video. Fast image-to-video conversion using Seedance V1 Lite. Quick AI image animation with camera control. Triggers: seedance lite image to video, seedance lite i2v, fast image to video, seedance lite, quick image animation"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1 | Lite | Image to Video

Fast image-to-video conversion using Seedance V1 Lite. A lighter, faster variant of Seedance V1 for quick image animation with camera control, last frame targeting, and resolution up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-lite-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset.jpg",
      "prompt": "Gentle waves lapping at the shore, sun slowly setting",
      "duration": 5,
      "resolution": "720p",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 9:16 | Aspect ratio. Options: `21:9`, `16:9`, `4:3`, `1:1`, `9:16` |
| camera_fixed | boolean | false | Whether to fix the camera position |
| duration | integer | 5 | Duration of the video in seconds |
| image_url | string | - | URL of the input image |
| last_frame_image | string | - | URL of the target last frame image |
| prompt | string | - | Text prompt to guide the animation |
| resolution | string | 720p | Video resolution. Options: `480p`, `720p`, `1080p` |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Quick portrait animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-lite-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Person smiling and nodding slightly, warm lighting",
      "aspect_ratio": "9:16",
      "resolution": "720p",
      "camera_fixed": true
    }
  }'
```

**Fast animation with end frame:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-lite-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/flower-bud.jpg",
      "last_frame_image": "https://example.com/flower-bloom.jpg",
      "prompt": "Flower slowly blooming open, time-lapse style",
      "duration": 5,
      "resolution": "480p"
    }
  }'
```

## Related Models

- [Seedance V1 | Pro | Image to Video](../seedance-v1-pro-image-to-video/) - Higher quality Pro variant
- [Seedance V1 | Lite | Text to Video](../seedance-v1-lite-text-to-video/) - Lite text-to-video
- [Wan 2.2 | Image to Video](../wan-2-2-i2v/) - Alternative image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
