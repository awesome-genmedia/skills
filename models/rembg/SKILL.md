---
name: rembg
description: "Rembg - Remove Background | AI Background Removal. Remove backgrounds from images automatically. Triggers: rembg, remove background, background removal, bg remove, transparent background"
allowed-tools: Bash(curl *), WebFetch
---

# Rembg - Remove Background

Remove backgrounds from images automatically using Rembg. Simply provide an image and receive a transparent background version.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rembg",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/product-photo.jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image | string | - | Input image to remove background from |

## Examples

**Remove background from product photo:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rembg",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/sneaker-on-table.jpg"
    }
  }'
```

**Remove background from portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "rembg",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/headshot-outdoor.jpg"
    }
  }'
```

## Related Models

- [realistic-background](../realistic-background/) - Replace backgrounds with AI-generated scenes
- [sdxl-ad-inpaint](../sdxl-ad-inpaint/) - Product ad image generation
- [flux-fill-pro](../flux-fill-pro/) - Inpainting and image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
