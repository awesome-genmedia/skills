---
name: seedance-v1-pro-fast-text-to-video
description: "Seedance V1 | Pro | Fast | Text to Video. Generate videos from text with fast inference using Seedance V1 Pro. Triggers: seedance, text to video, fast video, video generation, seedance pro"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1 | Pro | Fast | Text to Video

Generate high-quality videos from text prompts using the Seedance V1 Pro Fast model. Supports configurable aspect ratio, resolution, duration, and camera control for precise video output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-fast-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A butterfly landing on a sunflower in a garden, macro shot, golden hour lighting",
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
| prompt | string | | The text prompt used to generate the video |
| resolution | string | 1080p | Video resolution. enum: 480p, 720p, 1080p |
| seed | integer | | Random seed to control video generation |

## Examples

**Vertical video for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-fast-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A woman walking down a neon-lit alley in Tokyo at night, cinematic style",
      "aspect_ratio": "9:16",
      "resolution": "1080p",
      "duration": 5
    }
  }'
```

**Fixed camera scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-fast-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A steam train arriving at a Victorian-era station with passengers waiting on the platform",
      "aspect_ratio": "21:9",
      "resolution": "720p",
      "duration": 5,
      "camera_fixed": true,
      "seed": 12345
    }
  }'
```

## Related Models

- [seedance-v1-pro-fast-image-to-video](../seedance-v1-pro-fast-image-to-video/) - Image to video with Seedance V1 Pro Fast

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
