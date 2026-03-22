---
name: kling-v1-6-standard-elements
description: "Kling v1.6 | Standard | Elements. Generate creative element-based videos using Kling v1.6 | Standard | Elements. Triggers: kling, video effects, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v1.6 | Standard | Elements

Generate creative element-based videos using Kling v1.6 | Standard | Elements. Supports multiple aspect ratios (16:9, 9:16, 1:1), configurable duration, negative prompt support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-6-standard-elements",
    "version": "0.0.1",
    "input": {
      "prompt": "Magical sparkling particles floating around the subject",
      "input_image_urls": ["https://example.com/image1.jpg", "https://example.com/image2.jpg"]
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | 16:9 | Options: `16:9`, `9:16`, `1:1` |
| `duration` | integer | 5 |  |
| `input_image_urls` | array |  | List of image URLs to use for video generation. Supports up to 4 images. |
| `negative_prompt` | string |  |  |
| `prompt` | string |  |  |

## Examples

**Element-based video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-6-standard-elements",
    "version": "0.0.1",
    "input": {
      "prompt": "Magical sparkling particles floating around the subject",
      "input_image_urls": ["https://example.com/image1.jpg", "https://example.com/image2.jpg"]
    }
  }'
```

**Advanced element composition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-6-standard-elements",
    "version": "0.0.1",
    "input": {
      "prompt": "Fire and ice elements swirling around the character",
      "input_image_urls": ["https://example.com/image1.jpg", "https://example.com/image2.jpg"],
      "aspect_ratio": "9:16",
      "duration": 8,
      "negative_prompt": "blurry, distorted, low quality, watermark"
    }
  }'
```

## Related Models

- [Kling v1.6 | Pro | Elements](../kling-v1-6-pro-elements/) - Generate creative element-based videos using Kling v1.6 | Pro | Elements.
- [Kling v1.6 | Standard | Effects](../kling-v1-6-standart-effects/) - Apply visual effects to images and generate videos using Kling v1.6 | Standard | Effects.
- [Kling v1.6 | Pro | Effects](../kling-v1-6-pro-effects/) - Apply visual effects to images and generate videos using Kling v1.6 | Pro | Effects.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
