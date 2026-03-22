---
name: real-esrgan
description: "Real Esrgan - Face Enhancer | Image Upscaling and Face Enhancement. Upscale images and enhance faces using Real-ESRGAN with GFPGAN. Triggers: real esrgan, face enhancer, upscale, image enhance, super resolution"
allowed-tools: Bash(curl *), WebFetch
---

# Real Esrgan - Face Enhancer

Upscale images and optionally enhance faces using Real-ESRGAN with GFPGAN face enhancement. Simple and effective image upscaling with configurable scale factor.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "real-esrgan",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/low-res-photo.jpg",
      "scale": 4,
      "face_enhance": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| face_enhance | boolean | false | Run GFPGAN face enhancement along with upscaling |
| image | string | - | Input image |
| scale | number | 4 | Factor to scale image by |

## Examples

**Upscale with face enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "real-esrgan",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/old-family-photo.jpg",
      "scale": 4,
      "face_enhance": true
    }
  }'
```

**Simple 2x upscale without face enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "real-esrgan",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/landscape-thumbnail.jpg",
      "scale": 2,
      "face_enhance": false
    }
  }'
```

## Related Models

- [real-esrgan-a100](../real-esrgan-a100/) - Faster face enhancement on A100 GPU
- [gfpgan](../gfpgan/) - Dedicated GFPGAN face restoration
- [each-upscaler](../each-upscaler/) - Advanced upscaler with creativity controls

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
