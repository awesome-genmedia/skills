---
name: gfpgan
description: "GFPGAN | AI Face Restoration. Restore and enhance faces in images with multiple model versions. Triggers: gfpgan, face restoration, face enhance, photo restore, face repair"
allowed-tools: Bash(curl *), WebFetch
---

# GFPGAN

Restore and enhance faces in images using GFPGAN. Supports multiple model versions including RestoreFormer for high-quality face restoration with configurable rescaling.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gfpgan",
    "version": "0.0.1",
    "input": {
      "img": "https://example.com/old-photo-with-faces.jpg",
      "version": "v1.4",
      "scale": 2
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| img | string | - | Input image |
| scale | number | 2 | Rescaling factor |
| version | string | v1.4 | GFPGAN model version. enum: v1.2, v1.3, v1.4, RestoreFormer |

## Examples

**Restore old family photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gfpgan",
    "version": "0.0.1",
    "input": {
      "img": "https://example.com/vintage-family-photo.jpg",
      "version": "v1.4",
      "scale": 4
    }
  }'
```

**RestoreFormer for heavy restoration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gfpgan",
    "version": "0.0.1",
    "input": {
      "img": "https://example.com/damaged-portrait.jpg",
      "version": "RestoreFormer",
      "scale": 2
    }
  }'
```

## Related Models

- [real-esrgan](../real-esrgan/) - Image upscaling with face enhancement
- [real-esrgan-a100](../real-esrgan-a100/) - Fast face enhancement
- [each-upscaler](../each-upscaler/) - Advanced image upscaler

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
