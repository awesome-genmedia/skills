---
name: eachlabs-product-arc-shot-v1
description: "Eachlabs Product Arc Shot | v1. Create product arc shot videos from a single image. Automatic 360-degree rotating product showcase video. Triggers: product arc shot, product video, 360 product, rotating product, product showcase, arc shot, product rotation video"
allowed-tools: Bash(curl *), WebFetch
---

# Eachlabs Product Arc Shot | v1

Create product arc shot videos from a single image. Automatically generates a rotating 360-degree showcase video of your product, perfect for e-commerce listings and marketing materials.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-product-arc-shot-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | - | URL of the product image |

## Examples

**Sneaker showcase:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-product-arc-shot-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sneaker.jpg"
    }
  }'
```

**Electronics product rotation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-product-arc-shot-v1",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headphones.jpg"
    }
  }'
```

## Related Models

- [Product Shoot](../product-shoot/) - Generate product photography
- [Eachlabs Background Remover v1](../eachlabs-bg-remover-v1/) - Remove backgrounds before arc shot
- [Eachlabs Image Upscaler | Pro | v1](../eachlabs-image-upscaler-pro-v1/) - Upscale product images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
