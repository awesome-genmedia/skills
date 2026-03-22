---
name: pixverse-v4-5-image-to-video
description: "PixVerse v4.5 | Image to Video. Generate videos from images using PixVerse v4.5 | Image to Video. Triggers: image to video, pixverse, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# PixVerse v4.5 | Image to Video

Generate videos from images using PixVerse v4.5 | Image to Video. Supports configurable duration, negative prompt support, reproducible results via seed, style selection, quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Slow camera pan with gentle wind movement",
      "image_url": "https://example.com/your-image.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `duration` | integer | 5 |  |
| `image_url` | string |  |  |
| `lip_sync_switch` | boolean |  | Set to true if you want to enable this feature. Default is false. |
| `lip_sync_tts_content` | string |  | ~140 (UTF-8) characters |
| `lip_sync_tts_speaker_id` | string |  |  |
| `motion_mode` | string | normal | Options: `normal`, `fast` |
| `negative_prompt` | string |  |  |
| `prompt` | string |  |  |
| `quality` | string | 540p | Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer |  | Set a seed for reproducibility. Random by default. |
| `sound_effect_content` | string |  |  |
| `sound_effect_switch` | boolean | True |  |
| `style` | string |  | Options: `anime`, `3d_animation`, `clay`, `comic`, `cyberpunk` |

## Examples

**Animate an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Slow camera pan with gentle wind movement",
      "image_url": "https://example.com/your-image.jpg"
    }
  }'
```

**Dynamic animation with controls:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Dynamic camera zoom with dramatic lighting changes",
      "image_url": "https://example.com/your-image.jpg",
      "duration": 8,
      "negative_prompt": "blurry, distorted, low quality, watermark",
      "style": "anime",
      "seed": 42,
      "quality": "1080p",
      "motion_mode": "fast"
    }
  }'
```

## Related Models

- [PixVerse v4.5 | Effect](../pixverse-v4-5-effect/) - Apply visual effects to images and generate videos using PixVerse v4.5 | Effect.
- [PixVerse v4.5 | Transition](../pixverse-v4-5-transition/) - Create smooth video transitions between images using PixVerse v4.5 | Transition.
- [PixVerse v4.5 | Text to Video](../pixverse-v4-5-text-to-video/) - Generate videos from text descriptions using PixVerse v4.5 | Text to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
