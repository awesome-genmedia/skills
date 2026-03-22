---
name: eachlabs-bg-remover-v1
description: "Eachlabs Background Remover v1. Remove backgrounds from images using AI. One-click background removal for any image. Triggers: remove background, background remover, bg remover, cut out, background removal, transparent background, eachlabs bg remove"
allowed-tools: Bash(curl *), WebFetch
---

# Eachlabs Background Remover v1

Remove backgrounds from images using AI. A simple one-click solution for removing backgrounds, producing transparent PNG output perfect for product photos, portraits, and design assets.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-bg-remover-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | - | URL of the image to remove the background from |

## Examples

**Remove background from a product photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-bg-remover-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/shoe-on-table.jpg"
    }
  }'
```

**Remove background from a portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-bg-remover-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headshot.jpg"
    }
  }'
```

## Related Models

- [Product Shoot](../product-shoot/) - Generate product photos with new backgrounds
- [Eachlabs Product Arc Shot | v1](../eachlabs-product-arc-shot-v1/) - Create product arc shot videos
- [Eachlabs Image Upscaler | Pro | v1](../eachlabs-image-upscaler-pro-v1/) - Upscale images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
