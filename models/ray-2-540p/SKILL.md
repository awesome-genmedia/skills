---
name: ray-2-540p
description: "Luma | Ray2 | 540p. Generate video content using Luma | Ray2 | 540p. Triggers: luma ray, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Luma | Ray2 | 540p

Generate video content using Luma | Ray2 | 540p. Supports multiple aspect ratios (1:1, 3:4, 4:3, 9:16, 16:9, 9:21, 21:9), configurable duration.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ray-2-540p",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic establishing shot of a futuristic city",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | An enumeration.. Options: `1:1`, `3:4`, `4:3`, `9:16`, `16:9`, `9:21`, `21:9` |
| `duration` | integer | 5 | An enumeration. |
| `end_image_url` | string |  | Image to use as the ending frame |
| `loop` | boolean |  | Whether the video should loop, with the last frame matching the first frame for |
| `prompt` | string |  | Text prompt for video generation |
| `start_image_url` | string |  | image to use as the starting frame |

## Examples

**Basic generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ray-2-540p",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic establishing shot of a futuristic city",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg"
    }
  }'
```

**Advanced generation with options:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ray-2-540p",
    "version": "0.0.1",
    "input": {
      "prompt": "An intimate close-up of raindrops falling on a window",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg",
      "aspect_ratio": "9:16",
      "duration": 8
    }
  }'
```

## Related Models

- [Luma | Ray2 | 720p](../ray-2-720p/) - Generate video content using Luma | Ray2 | 720p.
- [Ray](../ray/) - Generate videos using Ray.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
