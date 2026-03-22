---
name: pixverse-v4-5-extend
description: "PixVerse v4.5 | Extend. Extend video duration using PixVerse v4.5 AI. Add more frames to existing videos with style and motion control. Triggers: extend video, video extension, pixverse extend, longer video, continue video, video continuation, pixverse v4.5"
allowed-tools: Bash(curl *), WebFetch
---

# PixVerse v4.5 | Extend

Extend the duration of existing videos using PixVerse v4.5. Seamlessly continue a video with AI-generated frames, with control over style, motion speed, quality, and optional prompt guidance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-extend",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/short-clip.mp4",
      "prompt": "Continue the scene with the camera slowly pulling back",
      "duration": 5,
      "quality": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | integer | 5 | Duration to extend in seconds |
| motion_mode | string | normal | Motion speed. Options: `normal`, `fast` |
| negative_prompt | string | - | Text describing what to avoid |
| prompt | string | - | Text prompt to guide the extension |
| quality | string | 720p | Output quality. Options: `360p`, `540p`, `720p`, `1080p` |
| seed | integer | - | Random seed for reproducible results |
| style | string | - | Visual style. Options: `anime`, `3d_animation`, `clay`, `comic`, `cyberpunk` |
| video_url | string | - | URL of the video to extend |

## Examples

**Extend with anime style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-extend",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/anime-clip.mp4",
      "prompt": "Character continues running through the rain",
      "style": "anime",
      "duration": 5,
      "quality": "1080p",
      "motion_mode": "fast"
    }
  }'
```

**Extend with negative prompt for quality control:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-extend",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/nature-scene.mp4",
      "prompt": "The sun continues to set behind the mountains",
      "negative_prompt": "blurry, glitch, artifacts, distortion",
      "quality": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [PixVerse | Lip Sync](../pixverse-lip-sync/) - Lip sync audio to video
- [Google Veo 3](../veo-3/) - Text-to-video generation
- [Runway | Gen4 | Turbo](../gen4-turbo/) - Fast video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
