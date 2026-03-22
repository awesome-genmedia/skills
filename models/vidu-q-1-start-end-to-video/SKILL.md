---
name: vidu-q-1-start-end-to-video
description: "Vidu Q1 | Start End to Video. Generate videos from start and end frame images using Vidu Q1 | Start End to Video. Triggers: start end to video, video generation, vidu"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu Q1 | Start End to Video

Generate videos from start and end frame images using Vidu Q1 | Start End to Video. Supports configurable duration, reproducible results via seed, configurable resolution, movement amplitude control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-start-end-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Smooth transition between the two frames with natural motion",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `bgm` | boolean |  | Whether to add background music to the generated video. |
| `duration` | integer | 5 | Video duration. |
| `end_image_url` | string |  | End Image Url |
| `movement_amplitude` | string | auto | The movement amplitude of objects in the frame. Options: `auto`, `small`, `medium`, `large` |
| `prompt` | string |  | Prompt description, max 1500 characters. |
| `resolution` | string | 1080p | Resolution. Options: `1080p` |
| `seed` | integer |  | Seed |
| `start_image_url` | string |  | Start Image Url |

## Examples

**Frame interpolation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-start-end-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Smooth transition between the two frames with natural motion",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg"
    }
  }'
```

**Dramatic transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-start-end-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Dramatic transformation with cinematic camera movement",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg",
      "duration": 8,
      "resolution": "1080p",
      "movement_amplitude": "large",
      "seed": 42
    }
  }'
```

## Related Models

- [Vidu Q1 | Image to Video](../vidu-q-1-image-to-video/) - Generate videos from images using Vidu Q1 | Image to Video.
- [Vidu 1.5 | Image to Video](../vidu-1-5-image-to-video/) - Generate videos from images using Vidu 1.5 | Image to Video.
- [Vidu 1.5 | Reference to Video](../vidu-1-5-reference-to-video/) - Generate videos using reference images with Vidu 1.5 | Reference to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
