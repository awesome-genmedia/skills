---
name: minimax-hailuo-v2-pro-image-to-video
description: "Minimax Hailuo V2 | Pro | Image to Video. Convert images to high-quality videos using Minimax Hailuo V2 Pro. Premium AI image-to-video generation. Triggers: hailuo pro image to video, minimax pro i2v, hailuo v2 pro, minimax pro image to video, premium image animation"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2 | Pro | Image to Video

Convert images to high-quality videos using Minimax Hailuo V2 Pro. The premium tier of Hailuo V2 for image-to-video generation, offering the highest quality output with prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Person slowly turning their head, smiling, hair flowing in the breeze"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | - | URL of the input image |
| prompt | string | - | Text prompt to guide the animation |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer |

## Examples

**Animate a product photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/watch-product.jpg",
      "prompt": "The watch rotating slowly on a reflective surface, light catching the metal details",
      "prompt_optimizer": true
    }
  }'
```

**Animate a painting:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/oil-painting.jpg",
      "prompt": "The painted scene comes to life, clouds drifting, trees swaying gently"
    }
  }'
```

## Related Models

- [Minimax Hailuo V2 | Standard | Image to Video](../minimax-hailuo-v2-standard-image-to-video/) - Standard tier (faster)
- [Minimax Hailuo V2 | Pro | Text to Video](../minimax-hailuo-v2-pro-text-to-video/) - Pro text-to-video
- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Google's image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
