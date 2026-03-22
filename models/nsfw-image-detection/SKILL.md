---
name: nsfw-image-detection
description: "NSFW Image Detection | Content Safety Analysis. Detect NSFW content in images for moderation and safety purposes. Triggers: nsfw detection, content moderation, image safety, nsfw check, content filter"
allowed-tools: Bash(curl *), WebFetch
---

# NSFW Image Detection

Analyze images for NSFW content. Use this model for content moderation, safety filtering, and automated image screening workflows.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nsfw-image-detection",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/photo-to-check.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image | string | - | Input image to analyze |

## Examples

**Check uploaded user content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nsfw-image-detection",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/user-upload.jpg"
    }
  }'
```

**Moderate generated images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nsfw-image-detection",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/generated-image.png"
    }
  }'
```

## Related Models

- [blip-2](../blip-2/) - Image captioning and visual Q&A
- [1019-face-analyzer](../1019-face-analyzer/) - Face analysis for age, race, and gender
- [rembg](../rembg/) - Background removal from images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
