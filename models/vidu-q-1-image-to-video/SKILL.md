---
name: vidu-q-1-image-to-video
description: "Vidu Q1 | Image to Video. Generate videos from images using Vidu Q1 | Image to Video. Triggers: image to video, video generation, vidu"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu Q1 | Image to Video

Generate videos from images using Vidu Q1 | Image to Video. Supports configurable duration, reproducible results via seed, configurable resolution, movement amplitude control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-image-to-video",
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
| `bgm` | boolean |  | Whether to add background music to the generated video. |
| `duration` | integer | 5 | Video duration |
| `image_url` | string |  | Image Url |
| `movement_amplitude` | string | auto | The movement amplitude of objects in the frame. Options: `auto`, `small`, `medium`, `large` |
| `prompt` | string |  | Text prompt,A textual description for video generation, with a maximum length of |
| `resolution` | string | 1080p | Resolution. Options: `1080p` |
| `seed` | integer |  | Seed |

## Examples

**Animate an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-q-1-image-to-video",
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
    "model": "vidu-q-1-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Dynamic camera zoom with dramatic lighting changes",
      "image_url": "https://example.com/your-image.jpg",
      "duration": 8,
      "resolution": "1080p",
      "movement_amplitude": "large",
      "seed": 42
    }
  }'
```

## Related Models

- [Vidu Q1 | Start End to Video](../vidu-q-1-start-end-to-video/) - Generate videos from start and end frame images using Vidu Q1 | Start End to Video.
- [Vidu 1.5 | Image to Video](../vidu-1-5-image-to-video/) - Generate videos from images using Vidu 1.5 | Image to Video.
- [Vidu 1.5 | Reference to Video](../vidu-1-5-reference-to-video/) - Generate videos using reference images with Vidu 1.5 | Reference to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
