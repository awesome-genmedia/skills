---
name: product-shoot
description: "Product Shoot. Generate professional product photography using AI. Create studio-quality product images from reference photos and text prompts. Triggers: product photography, product shoot, product photo, ai product image, commercial photography, product visualization, e-commerce photo"
allowed-tools: Bash(curl *), WebFetch
---

# Product Shoot

Generate professional product photography using AI. Upload up to 2 product images and provide a text prompt to create studio-quality product shots with customizable aspect ratios, perfect for e-commerce and marketing.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "product-shoot",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/sneaker.jpg",
      "prompt": "Premium sneaker on a marble surface with dramatic studio lighting, clean white background, commercial product photography",
      "aspect_ratio": "1:1"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | match_input_image | Output aspect ratio. Options: `match_input_image`, `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `4:5`, `5:4`, `21:9`, `9:21`, `2:1`, `1:2` |
| input_image_1 | string | - | First input image. Must be jpeg, png, gif, or webp |
| input_image_2 | string | - | Second input image. Must be jpeg, png, gif, or webp |
| prompt | string | - | Text prompt describing the desired product shot |

## Examples

**E-commerce product shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "product-shoot",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/perfume-bottle.jpg",
      "prompt": "Luxury perfume bottle on a reflective black surface with golden bokeh lights in the background, premium product photography",
      "aspect_ratio": "4:5"
    }
  }'
```

**Product with lifestyle context:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "product-shoot",
    "version": "0.0.1",
    "input": {
      "input_image_1": "https://example.com/coffee-mug.jpg",
      "input_image_2": "https://example.com/coffee-beans.jpg",
      "prompt": "Artisan coffee mug next to fresh coffee beans on a rustic wooden table, warm morning light streaming through a window, cozy atmosphere",
      "aspect_ratio": "16:9"
    }
  }'
```

## Related Models

- [Eachlabs Product Arc Shot | v1](../eachlabs-product-arc-shot-v1/) - Product arc shot videos
- [Eachlabs Background Remover v1](../eachlabs-bg-remover-v1/) - Remove image backgrounds
- [Flux.1 Kontext | Pro](../flux-kontext-pro/) - AI image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
