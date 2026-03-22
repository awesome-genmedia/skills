---
name: seedance-v1-pro-text-to-video
description: "Seedance V1 | Pro | Text to Video. Generate high-quality videos from text prompts using Seedance V1 Pro. Professional AI text-to-video with camera control. Triggers: seedance text to video, seedance pro t2v, seedance v1 pro video, text to video seedance, professional text to video"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1 | Pro | Text to Video

Generate high-quality videos from text descriptions using Seedance V1 Pro. Professional-grade text-to-video generation with control over camera movement, duration, aspect ratio, and resolution up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A spaceship launching from a desert planet, dust clouds billowing, camera tracking upward",
      "aspect_ratio": "16:9",
      "duration": 5,
      "resolution": "1080p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. Options: `21:9`, `16:9`, `4:3`, `1:1`, `9:16` |
| camera_fixed | boolean | false | Whether to fix the camera position |
| duration | integer | 5 | Duration of the video in seconds |
| prompt | string | - | Text prompt for video generation |
| resolution | string | 1080p | Video resolution. Options: `480p`, `720p`, `1080p` |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Epic nature documentary shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A polar bear walking across Arctic ice, breath visible in the cold air, dramatic natural lighting, nature documentary cinematography",
      "aspect_ratio": "21:9",
      "duration": 5,
      "resolution": "1080p",
      "camera_fixed": false
    }
  }'
```

**Static camera scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A candle flame flickering in a dark room, wax slowly melting, intimate close-up",
      "camera_fixed": true,
      "aspect_ratio": "1:1",
      "duration": 5,
      "seed": 42
    }
  }'
```

## Related Models

- [Seedance V1 | Lite | Text to Video](../seedance-v1-lite-text-to-video/) - Faster Lite variant
- [Seedance V1 | Pro | Image to Video](../seedance-v1-pro-image-to-video/) - Pro image-to-video
- [Google Veo 3](../veo-3/) - Google's text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
