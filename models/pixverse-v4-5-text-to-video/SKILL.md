---
name: pixverse-v4-5-text-to-video
description: "PixVerse v4.5 | Text to Video. Generate videos from text descriptions using PixVerse v4.5 | Text to Video. Triggers: pixverse, text to video, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# PixVerse v4.5 | Text to Video

Generate videos from text descriptions using PixVerse v4.5 | Text to Video. Supports multiple aspect ratios (16:9, 4:3, 1:1, 3:4, 9:16), configurable duration, negative prompt support, reproducible results via seed, style selection, quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with cherry blossoms falling gently in the wind"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | The video’s width-to-height ratio. Options: `16:9`, `4:3`, `1:1`, `3:4`, `9:16` |
| `duration` | string | 5 | Length of the video in seconds.. Options: `5`, `8` |
| `lip_sync_switch` | boolean |  | Set to true if you want to enable this feature. Default is false. |
| `lip_sync_tts_content` | string |  | ~140 (UTF-8) characters |
| `lip_sync_tts_speaker_id` | string |  |  |
| `motion_mode` | string | normal | Controls animation speed. Options: `normal`, `fast` |
| `negative_prompt` | string |  | Text for things you don’t want to appear in the video. <= 2048 characters |
| `prompt` | string |  | Text description of the scene or video you want to create. <= 2048 characters |
| `quality` | string | 540p | The resolution quality of the video.. Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer |  |  |
| `sound_effect_content` | string |  |  |
| `sound_effect_switch` | boolean | True |  |
| `style` | string |  | Visual style for the video. Options: `anime`, `3d_animation`, `clay`, `comic`, `cyberpunk` |

## Examples

**Nature scene video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with cherry blossoms falling gently in the wind"
    }
  }'
```

**Cinematic aerial shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-5-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Cinematic drone shot flying over a misty mountain range at golden hour, volumetric lighting",
      "aspect_ratio": "9:16",
      "duration": "10",
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
- [PixVerse v4.5 | Image to Video](../pixverse-v4-5-image-to-video/) - Generate videos from images using PixVerse v4.5 | Image to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
