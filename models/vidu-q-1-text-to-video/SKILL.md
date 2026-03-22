---
name: vidu-q-1-text-to-video
description: "Vidu Q1 | Text to Video. Generate videos from text descriptions using Vidu Q1 | Text to Video. Triggers: text to video, video generation, vidu"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu Q1 | Text to Video

Generate videos from text descriptions using Vidu Q1 | Text to Video. Supports multiple aspect ratios (16:9, 9:16, 1:1), configurable duration, reproducible results via seed, configurable resolution, style selection, movement amplitude control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with cherry blossoms falling gently in the wind"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | Options: `16:9`, `9:16`, `1:1` |
| `bgm` | boolean |  | Whether to add background music to the generated video. |
| `duration` | integer | 5 | Video duration. |
| `movement_amplitude` | string | auto | Options: `auto`, `small`, `medium`, `large` |
| `prompt` | string |  |  |
| `resolution` | string | 1080p | Resolution. Options: `1080p` |
| `seed` | integer |  | Seed |
| `style` | string | general | The style of output video. Options: `general`, `anime` |

## Examples

**Nature scene video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-text-to-video",
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
    "model": "vidu-q-1-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Cinematic drone shot flying over a misty mountain range at golden hour, volumetric lighting",
      "aspect_ratio": "9:16",
      "duration": 8,
      "resolution": "1080p",
      "movement_amplitude": "large",
      "style": "anime",
      "seed": 42
    }
  }'
```

## Related Models

- [Vidu Q1 | Start End to Video](../vidu-q-1-start-end-to-video/) - Generate videos from start and end frame images using Vidu Q1 | Start End to Video.
- [Vidu Q1 | Image to Video](../vidu-q-1-image-to-video/) - Generate videos from images using Vidu Q1 | Image to Video.
- [Vidu 1.5 | Image to Video](../vidu-1-5-image-to-video/) - Generate videos from images using Vidu 1.5 | Image to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
