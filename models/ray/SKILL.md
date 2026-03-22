---
name: ray
description: "Ray. Generate videos using Ray. Triggers: luma ray, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Ray

Generate videos using Ray. Supports multiple aspect ratios (1:1, 3:4, 4:3, 9:16, 16:9, 9:21, 21:9).

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ray",
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
| `end_image_url` | string |  | URL of an image to use as the ending frame |
| `end_video_id` | string |  | Prepend a new video generation to the beginning of an existing one (Also called |
| `loop` | boolean |  | Whether the video should loop |
| `prompt` | string |  | Text prompt for video generation |
| `start_image_url` | string |  | URL of an image to use as the starting frame |
| `start_video_id` | string |  | Continue or extend a video generation with a new generation. You can combine thi |

## Examples

**Generate a cinematic video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ray",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic establishing shot of a futuristic city",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg"
    }
  }'
```

**Detailed scene video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ray",
    "version": "0.0.1",
    "input": {
      "prompt": "An intimate close-up of raindrops falling on a window",
      "start_image_url": "https://example.com/start-frame.jpg",
      "end_image_url": "https://example.com/end-frame.jpg",
      "aspect_ratio": "9:16"
    }
  }'
```

## Related Models

- [Luma | Ray2 | 540p](../ray-2-540p/) - Generate video content using Luma | Ray2 | 540p.
- [Luma | Ray2 | 720p](../ray-2-720p/) - Generate video content using Luma | Ray2 | 720p.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
