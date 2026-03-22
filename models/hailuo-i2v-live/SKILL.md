---
name: hailuo-i2v-live
description: "Hailuo Live | Image to Video. Generate videos from images using Hailuo Live | Image to Video. Triggers: hailuo, image to video, live portrait, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Hailuo Live | Image to Video

Generate videos from images using Hailuo Live | Image to Video. Supports optional prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "hailuo-i2v-live",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `first_frame_image` | string |  | First frame image for video generation. The output video will have the same aspe |
| `prompt` | string |  | Enter your prompt to generate video |
| `prompt_optimizer` | boolean | True | The model will automatically optimize prompts to improve generation quality. To |

## Examples

**Animate an image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "hailuo-i2v-live",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg"
    }
  }'
```

**Dynamic animation with controls:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "hailuo-i2v-live",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Expressive facial movements with a warm smile"
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
