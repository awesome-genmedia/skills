---
name: eachlabs-image-upscaler-pro-v1
description: "Eachlabs Image Upscaler | Pro | v1. Upscale images using Eachlabs Pro upscaler. Simple one-click AI image upscaling with configurable scale factor and format. Triggers: image upscaler, upscale image, eachlabs upscale, pro upscaler, enhance resolution, increase image size, super resolution"
allowed-tools: Bash(curl *), WebFetch
---

# Eachlabs Image Upscaler | Pro | v1

Upscale images using the Eachlabs Pro image upscaler. A simple, one-click solution for increasing image resolution with configurable scale factor and output format.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-image-upscaler-pro-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/small-photo.jpg",
      "upscale_factor": 2,
      "output_format": "PNG"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | - | URL of the image to upscale |
| output_format | string | PNG | Output format. Options: `JPG`, `PNG`, `WEBP` |
| upscale_factor | integer | 2 | Scale factor for upscaling |

## Examples

**2x upscale to PNG:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-image-upscaler-pro-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/low-res-portrait.jpg",
      "upscale_factor": 2,
      "output_format": "PNG"
    }
  }'
```

**4x upscale to WEBP:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-image-upscaler-pro-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/thumbnail.jpg",
      "upscale_factor": 4,
      "output_format": "WEBP"
    }
  }'
```

## Related Models

- [CCSR Upscaler](../ccsr/) - Advanced upscaler with tiling and color correction
- [Eachlabs Background Remover v1](../eachlabs-bg-remover-v1/) - Remove image backgrounds
- [Eachlabs Product Arc Shot | v1](../eachlabs-product-arc-shot-v1/) - Product arc shot videos

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
