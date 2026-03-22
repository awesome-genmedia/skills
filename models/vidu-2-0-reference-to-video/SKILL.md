---
name: vidu-2-0-reference-to-video
description: "Vidu 2.0 | Reference to Video. Generate videos using reference images with Vidu 2.0 | Reference to Video. Triggers: reference to video, video generation, vidu"
allowed-tools: Bash(curl *), WebFetch
---

# Vidu 2.0 | Reference to Video

Generate videos using reference images with Vidu 2.0 | Reference to Video. Supports multiple aspect ratios (16:9, 9:16, 1:1), configurable duration, reproducible results via seed, configurable resolution, movement amplitude control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-2-0-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A person walking through a vibrant autumn forest",
      "image_url": "https://example.com/your-image.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | Options: `16:9`, `9:16`, `1:1` |
| `duration` | integer | 4 | The number of seconds of duration for the output video |
| `image_url` | string |  | The model will use the provided images as references to generate a video with co |
| `image_url2` | string |  |  |
| `image_url3` | string |  |  |
| `image_url4` | string |  |  |
| `movement_amplitude` | string | auto | The movement amplitude of objects in the frame. Options: `auto`, `small`, `medium`, `large` |
| `prompt` | string |  | Text prompt, A textual description for video generation, with a maximum length o |
| `resolution` | string | 720p | Options: `720p` |
| `seed` | integer |  | Seed |

## Examples

**Reference-guided generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-2-0-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A person walking through a vibrant autumn forest",
      "image_url": "https://example.com/your-image.jpg"
    }
  }'
```

**Creative scene with references:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "vidu-2-0-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A dancer performing gracefully in a spotlight on a dark stage",
      "image_url": "https://example.com/your-image.jpg",
      "aspect_ratio": "9:16",
      "duration": 8,
      "movement_amplitude": "large",
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
