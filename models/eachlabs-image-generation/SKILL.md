---
name: eachlabs-image-generation
description: "Eachlabs Image Generation. Generate images from text prompts using Eachlabs Image Generation. Triggers: eachlabs, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Eachlabs Image Generation

Generate images from text prompts using Eachlabs Image Generation. Supports multiple aspect ratios (1:1, 2:3, 3:2).

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-image-generation",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic snow-capped mountain reflected in a crystal clear lake at sunrise",
      "image_url_1": "https://example.com/your-image.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string |  | Options: `1:1`, `2:3`, `3:2` |
| `image_url_1` | string |  |  |
| `image_url_10` | string |  |  |
| `image_url_2` | string |  |  |
| `image_url_3` | string |  |  |
| `image_url_4` | string |  |  |
| `image_url_5` | string |  |  |
| `image_url_6` | string |  |  |
| `image_url_7` | string |  |  |
| `image_url_8` | string |  |  |
| `image_url_9` | string |  |  |
| `prompt` | string |  |  |

## Examples

**Generate a landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-image-generation",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic snow-capped mountain reflected in a crystal clear lake at sunrise",
      "image_url_1": "https://example.com/your-image.jpg"
    }
  }'
```

**Detailed scene with style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-image-generation",
    "version": "0.0.1",
    "input": {
      "prompt": "A cyberpunk street market at night with holographic signs and rain-slicked roads, ultra detailed",
      "image_url_1": "https://example.com/your-image.jpg",
      "aspect_ratio": "9:16"
    }
  }'
```

## Related Models

- [Eachlabs Face Swap](../each-faceswap-v1/) - Swap faces in images using Eachlabs Face Swap.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
