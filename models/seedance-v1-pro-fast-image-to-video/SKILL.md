---
name: seedance-v1-pro-fast-image-to-video
description: "Seedance V1 | Pro | Fast | Image to Video. Animate images into videos with fast inference using Seedance V1 Pro. Triggers: seedance, image to video, animate image, fast video, seedance pro"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1 | Pro | Fast | Image to Video

Animate still images into dynamic videos using the Seedance V1 Pro Fast model. Supports configurable aspect ratio, resolution, duration, and camera control for precise video output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-fast-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "prompt": "The subject slowly turns and smiles, hair gently blowing in the wind",
      "aspect_ratio": "16:9",
      "resolution": "1080p",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 16:9, 4:3, 1:1, 9:16, 21:9 |
| camera_fixed | boolean | false | Whether to fix the camera position |
| duration | integer | 5 | Duration of the video in seconds |
| image_url | string | | The URL of the image used to generate video |
| prompt | string | | The text prompt used to generate the video |
| resolution | string | 1080p | Video resolution. enum: 480p, 720p, 1080p |
| seed | integer | | Random seed to control video generation |

## Examples

**Landscape animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-fast-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/mountain-scene.jpg",
      "prompt": "Clouds move slowly across the sky, birds fly in the distance",
      "aspect_ratio": "16:9",
      "resolution": "1080p",
      "duration": 5,
      "camera_fixed": true
    }
  }'
```

**Portrait animation with fast resolution:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-fast-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Person nods gently and blinks naturally",
      "aspect_ratio": "9:16",
      "resolution": "480p",
      "duration": 5,
      "seed": 42
    }
  }'
```

## Related Models

- [seedance-v1-pro-fast-text-to-video](../seedance-v1-pro-fast-text-to-video/) - Text to video with Seedance V1 Pro Fast

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
