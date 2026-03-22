---
name: minimax-hailuo-v2-3-fast-pro-image-to-video
description: "Minimax Hailuo V2.3 | Fast | Pro | Image to Video. Fast pro-quality image-to-video generation. Triggers: image to video, minimax, hailuo, fast, pro, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2.3 | Fast | Pro | Image to Video

Generate videos from images with fast pro-quality output using Minimax Hailuo V2.3. Features built-in prompt optimization for better results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-fast-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/scene.jpg",
      "prompt": "camera slowly pans right, gentle breeze moves the leaves",
      "prompt_optimizer": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | | URL of the image to use as the first frame. |
| prompt | string | | Text prompt for video generation. |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer. |

## Examples

**Optimized generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-fast-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "person slowly turns head and smiles warmly",
      "prompt_optimizer": true
    }
  }'
```

**Manual prompt control:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-fast-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "clouds drift slowly across the sky, rays of sunlight break through",
      "prompt_optimizer": false
    }
  }'
```

## Related Models

- [Minimax Hailuo V2.3 | Fast | Standard | Image to Video](../minimax-hailuo-v2-3-fast-standard-image-to-video/) - Standard fast variant
- [Minimax Hailuo V2.3 | Pro | Image to Video](../minimax-hailuo-v2-3-pro-image-to-video/) - Pro quality (non-fast)

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
