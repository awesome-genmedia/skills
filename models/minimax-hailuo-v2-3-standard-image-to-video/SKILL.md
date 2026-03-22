---
name: minimax-hailuo-v2-3-standard-image-to-video
description: "Minimax Hailuo V2.3 | Standard | Image to Video. Animate images into videos using the Minimax Hailuo V2.3 Standard model. Triggers: minimax, hailuo, image to video, animate image, hailuo standard"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2.3 | Standard | Image to Video

Animate still images into dynamic videos using the Minimax Hailuo V2.3 Standard model. Supports configurable duration and prompt-guided motion with optional prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Camera slowly pans across the landscape as clouds drift overhead",
      "duration": "6",
      "prompt_optimizer": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| duration | string | 6 | The duration of the video in seconds. enum: 6, 10 |
| image_url | string | | URL of the image to use as the first frame |
| prompt | string | | Text prompt for video generation |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer |

## Examples

**Short animated landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/mountain-lake.jpg",
      "prompt": "Gentle ripples spread across the lake surface as a bird flies overhead",
      "duration": "6"
    }
  }'
```

**Extended portrait animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Person slowly turns their head and smiles naturally at the camera",
      "duration": "10",
      "prompt_optimizer": true
    }
  }'
```

## Related Models

- [minimax-hailuo-v2-3-standard-text-to-video](../minimax-hailuo-v2-3-standard-text-to-video/) - Standard tier text to video
- [minimax-hailuo-v2-3-pro-text-to-video](../minimax-hailuo-v2-3-pro-text-to-video/) - Pro tier text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
