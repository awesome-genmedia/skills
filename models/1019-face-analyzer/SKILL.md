---
name: 1019-face-analyzer
description: "Face Analyzer by Eachlabs | AI Face Analysis. Analyze faces in photos for age, race, and gender information. Triggers: face analyzer, face analysis, age detection, face detection, facial analysis"
allowed-tools: Bash(curl *), WebFetch
---

# Face Analyzer by Eachlabs

Analyze faces in photos to extract information about age, race, and gender. Provide a face photo URL and receive detailed facial attribute analysis.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "1019-face-analyzer",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/face-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | - | Photo of a face to analyze for age, race, and gender information |

## Examples

**Analyze a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "1019-face-analyzer",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headshot.jpg"
    }
  }'
```

**Analyze a group photo face:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "1019-face-analyzer",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/person-cropped.jpg"
    }
  }'
```

## Related Models

- [nsfw-image-detection](../nsfw-image-detection/) - Content safety analysis
- [blip-2](../blip-2/) - Image captioning and visual Q&A
- [face-swap-new](../face-swap-new/) - Face swapping between images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
