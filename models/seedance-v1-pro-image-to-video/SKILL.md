---
name: seedance-v1-pro-image-to-video
description: "Seedance V1 | Pro | Image to Video. Convert images to high-quality videos using Seedance V1 Pro. Professional AI image-to-video generation with camera control. Triggers: seedance image to video, seedance pro i2v, seedance v1 pro, image animation seedance, professional image to video"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1 | Pro | Image to Video

Convert images to high-quality videos using Seedance V1 Pro. Professional-grade image-to-video generation with control over camera movement, duration, aspect ratio, resolution up to 1080p, and optional last frame targeting.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Camera slowly zooming in while clouds drift across the sky",
      "duration": 5,
      "resolution": "1080p",
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
| resolution | string | 1080p | Video resolution. Options: `480p`, `720p`, `1080p` |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Cinematic image animation with fixed camera:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cafe-scene.jpg",
      "prompt": "People chatting and drinking coffee, steam rising from cups, ambient cafe atmosphere",
      "camera_fixed": true,
      "duration": 5,
      "resolution": "1080p",
      "aspect_ratio": "16:9"
    }
  }'
```

**Transition between two frames:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/daytime-city.jpg",
      "last_frame_image": "https://example.com/nighttime-city.jpg",
      "prompt": "Smooth transition from day to night, lights gradually turning on",
      "duration": 5,
      "aspect_ratio": "16:9"
    }
  }'
```

## Related Models

- [Seedance V1 | Lite | Image to Video](../seedance-v1-lite-image-to-video/) - Faster Lite variant
- [Seedance V1 | Pro | Text to Video](../seedance-v1-pro-text-to-video/) - Pro text-to-video
- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Google's image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
