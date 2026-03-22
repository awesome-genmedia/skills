---
name: pixverse-v4-transition
description: "PixVerse v4 | Transition. Create smooth video transitions between images using PixVerse v4 | Transition. Triggers: pixverse, video generation, video transition"
allowed-tools: Bash(curl *), WebFetch
---

# PixVerse v4 | Transition

Create smooth video transitions between images using PixVerse v4 | Transition. Supports configurable duration, reproducible results via seed, quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-transition",
    "version": "0.0.1",
    "input": {
      "prompt": "Smooth morph between two scenes",
      "first_frame_url": "https://example.com/first-frame.jpg",
      "last_frame_url": "https://example.com/last-frame.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `duration` | integer | 5 |  |
| `first_frame_url` | string |  |  |
| `last_frame_url` | string |  |  |
| `motion_mode` | string | normal | Controls animation speed. Options: `normal`, `fast` |
| `prompt` | string |  |  |
| `quality` | string | 540p | The resolution quality of the video.. Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer |  |  |

## Examples

**Smooth transition between frames:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-transition",
    "version": "0.0.1",
    "input": {
      "prompt": "Smooth morph between two scenes",
      "first_frame_url": "https://example.com/first-frame.jpg",
      "last_frame_url": "https://example.com/last-frame.jpg"
    }
  }'
```

**Custom transition settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v4-transition",
    "version": "0.0.1",
    "input": {
      "prompt": "Cinematic wipe transition with particle effects",
      "first_frame_url": "https://example.com/first-frame.jpg",
      "last_frame_url": "https://example.com/last-frame.jpg",
      "duration": 8,
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
