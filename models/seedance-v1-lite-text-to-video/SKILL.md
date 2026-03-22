---
name: seedance-v1-lite-text-to-video
description: "Seedance V1 | Lite | Text to Video. Fast text-to-video generation using Seedance V1 Lite. Quick AI video creation from text prompts. Triggers: seedance lite text to video, seedance lite t2v, fast text to video, seedance lite video, quick video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1 | Lite | Text to Video

Fast text-to-video generation using Seedance V1 Lite. A lighter, faster variant for creating videos from text prompts with control over camera movement, duration, aspect ratio, and resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-lite-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cat playing with a ball of yarn in a sunny living room",
      "aspect_ratio": "16:9",
      "duration": 5,
      "resolution": "720p"
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
| resolution | string | 720p | Video resolution. Options: `480p`, `720p`, `1080p` |
| seed | integer | - | Random seed for reproducible results. Use -1 for random |

## Examples

**Quick nature scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-lite-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A waterfall cascading down moss-covered rocks in a tropical jungle, misty atmosphere, birds flying through the scene",
      "aspect_ratio": "9:16",
      "duration": 5,
      "resolution": "720p"
    }
  }'
```

**Fixed camera interior shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-lite-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy fireplace crackling with warm flames, stockings hanging above, Christmas decorations",
      "camera_fixed": true,
      "aspect_ratio": "16:9",
      "seed": 42
    }
  }'
```

## Related Models

- [Seedance V1 | Pro | Text to Video](../seedance-v1-pro-text-to-video/) - Higher quality Pro variant
- [Seedance V1 | Lite | Image to Video](../seedance-v1-lite-image-to-video/) - Lite image-to-video
- [Minimax Hailuo V2 | Standard | Text to Video](../minimax-hailuo-v2-standard-text-to-video/) - Alternative text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
