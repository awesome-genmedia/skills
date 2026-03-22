---
name: real-esrgan-a100
description: "Face Enhancer Fast | Fast Image Upscaling and Face Enhancement. Quickly upscale images and enhance faces on fast hardware. Triggers: face enhancer fast, fast upscale, real esrgan fast, quick enhance, face restore"
allowed-tools: Bash(curl *), WebFetch
---

# Face Enhancer Fast

Quickly upscale images and enhance faces using Real-ESRGAN on fast A100 hardware. Same capabilities as Real-ESRGAN with faster processing times.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "real-esrgan-a100",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/low-res-portrait.jpg",
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

**Quick face enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "real-esrgan-a100",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/old-photo.jpg",
      "scale": 4,
      "face_enhance": true
    }
  }'
```

**2x upscale without face processing:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "real-esrgan-a100",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/product-image.jpg",
      "scale": 2,
      "face_enhance": false
    }
  }'
```

## Related Models

- [real-esrgan](../real-esrgan/) - Standard Real-ESRGAN upscaler
- [gfpgan](../gfpgan/) - Dedicated face restoration
- [each-upscaler](../each-upscaler/) - Advanced upscaler with creativity controls

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
