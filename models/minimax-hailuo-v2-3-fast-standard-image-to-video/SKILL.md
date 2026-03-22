---
name: minimax-hailuo-v2-3-fast-standard-image-to-video
description: "Minimax Hailuo V2.3 | Fast | Standard | Image to Video. Fast standard image-to-video with configurable duration. Triggers: image to video, minimax, hailuo, fast, standard, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2.3 | Fast | Standard | Image to Video

Generate videos from images at standard quality with fast speed. Supports 6 or 10-second durations with built-in prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-fast-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cityscape.jpg",
      "prompt": "cars moving through the street, city life in motion",
      "duration": "6"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | 6 | The duration of the video in seconds. enum: 6, 10 |
| image_url | string | | URL of the image to use as the first frame. |
| prompt | string | | Text prompt for video generation. |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer. |

## Examples

**Short animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-fast-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/flower.jpg",
      "prompt": "flower slowly blooms, petals unfurl",
      "duration": "6",
      "prompt_optimizer": true
    }
  }'
```

**Extended 10-second video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-fast-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/ocean.jpg",
      "prompt": "waves crashing on shore, camera slowly pulls back to reveal the full beach",
      "duration": "10"
    }
  }'
```

## Related Models

- [Minimax Hailuo V2.3 | Fast | Pro | Image to Video](../minimax-hailuo-v2-3-fast-pro-image-to-video/) - Pro fast variant
- [Minimax Hailuo V2.3 | Pro | Image to Video](../minimax-hailuo-v2-3-pro-image-to-video/) - Pro quality (non-fast)

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
