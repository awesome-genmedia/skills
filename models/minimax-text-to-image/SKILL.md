---
name: minimax-text-to-image
description: "Minimax | Text to Image. Generate images from text prompts using Minimax | Text to Image. Triggers: image generation, minimax, text to image"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax | Text to Image

Generate images from text prompts using Minimax | Text to Image. Supports multiple aspect ratios (1:1, 16:9, 4:3, 3:2, 2:3, 3:4, 9:16, 21:9), optional prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic snow-capped mountain reflected in a crystal clear lake at sunrise"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 1:1 | Image aspect ratio. Options: `1:1`, `16:9`, `4:3`, `3:2`, `2:3`, `3:4`, `9:16`, `21:9` |
| `num_images` | integer | 1 | Number of images to generate |
| `prompt` | string |  | Text prompt for generation |
| `prompt_optimizer` | boolean |  | Use prompt optimizer |

## Examples

**Generate a landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic snow-capped mountain reflected in a crystal clear lake at sunrise"
    }
  }'
```

**Detailed scene with style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cyberpunk street market at night with holographic signs and rain-slicked roads, ultra detailed",
      "aspect_ratio": "9:16"
    }
  }'
```

## Related Models

- [Minimax Hailuo V1 | Text to Video](../minimax-t2v-01/) - Generate videos from text descriptions using Minimax Hailuo V1 | Text to Video.
- [Minimax Hailuo V1 | Subject to Video](../minimax-s2v-01/) - Generate videos from subject reference images using Minimax Hailuo V1 | Subject to Video.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
