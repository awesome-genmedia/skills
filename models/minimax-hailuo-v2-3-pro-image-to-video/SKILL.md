---
name: minimax-hailuo-v2-3-pro-image-to-video
description: "Minimax Hailuo V2.3 | Pro | Image to Video. Pro-quality image-to-video generation with Hailuo V2.3. Triggers: image to video, minimax, hailuo, pro, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2.3 | Pro | Image to Video

Generate pro-quality videos from images using Minimax Hailuo V2.3. Features built-in prompt optimization for highest quality output.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/dramatic-landscape.jpg",
      "prompt": "cinematic camera movement revealing the vast landscape, epic scale",
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

**Cinematic portrait animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/model-portrait.jpg",
      "prompt": "subtle head movement, hair flowing gently, natural blinking",
      "prompt_optimizer": true
    }
  }'
```

**Product showcase:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product.jpg",
      "prompt": "camera rotates around the product, studio lighting highlights textures",
      "prompt_optimizer": false
    }
  }'
```

## Related Models

- [Minimax Hailuo V2.3 | Fast | Pro | Image to Video](../minimax-hailuo-v2-3-fast-pro-image-to-video/) - Faster pro variant
- [Minimax Hailuo V2.3 | Fast | Standard | Image to Video](../minimax-hailuo-v2-3-fast-standard-image-to-video/) - Fast standard variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
