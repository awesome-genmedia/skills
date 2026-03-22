---
name: kling-v1-6-pro-effects
description: "Kling v1.6 | Pro | Effects. Apply visual effects to images and generate videos using Kling v1.6 | Pro | Effects. Triggers: kling, video effects, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v1.6 | Pro | Effects

Apply visual effects to images and generate videos using Kling v1.6 | Pro | Effects. Supports configurable duration.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-6-pro-effects",
    "version": "0.0.1",
    "input": {
      "image_url_1": "https://example.com/your-image.jpg",
      "template_slug": "kiss",
      "image_url_2": "https://example.com/second-image.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `duration` | integer | 5 |  |
| `image_url_1` | string |  |  |
| `image_url_2` | string |  | This input is required when the template slug is one of the following: hug, kiss |
| `template_slug` | string | kiss | Options: `hug`, `kiss`, `heart_gesture`, `squish`, `expansion`, `fuzzyfuzzy`, `bloombloom`, `dizzydizzy` |

## Examples

**Apply visual effect:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-6-pro-effects",
    "version": "0.0.1",
    "input": {
      "image_url_1": "https://example.com/your-image.jpg",
      "template_slug": "kiss",
      "image_url_2": "https://example.com/second-image.jpg"
    }
  }'
```

**Different effect style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-6-pro-effects",
    "version": "0.0.1",
    "input": {
      "image_url_1": "https://example.com/your-image.jpg",
      "template_slug": "squish",
      "duration": 8
    }
  }'
```

## Related Models

- [Kling v1.6 | Pro | Elements](../kling-v1-6-pro-elements/) - Generate creative element-based videos using Kling v1.6 | Pro | Elements.
- [Kling v1.6 | Standard | Elements](../kling-v1-6-standard-elements/) - Generate creative element-based videos using Kling v1.6 | Standard | Elements.
- [Kling v1.6 | Standard | Effects](../kling-v1-6-standart-effects/) - Apply visual effects to images and generate videos using Kling v1.6 | Standard | Effects.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
