---
name: flux-2-pro
description: "Flux 2 Pro. Professional-grade text-to-image generation. Triggers: text to image, flux, pro, image generation, professional"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 Pro

Generate professional-quality images from text prompts with Flux 2 Pro. Offers streamlined controls with configurable safety tolerance for production-ready results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a photorealistic macro shot of morning dew on a rose petal",
      "image_size": "landscape_4_3",
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| image_size | string | landscape_4_3 | The size of the generated image. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| output_format | string | jpeg | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate an image from. |
| safety_tolerance | string | 2 | The safety tolerance level. 1 is most strict, 5 is most permissive. enum: 1, 2, 3, 4, 5 |
| seed | integer | | The seed to use for the generation. |

## Examples

**Portrait generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "cinematic portrait of a jazz musician playing saxophone, dramatic rim lighting, moody atmosphere",
      "image_size": "portrait_16_9",
      "output_format": "png",
      "seed": 42
    }
  }'
```

**Product photography:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "luxury watch on a marble surface, studio lighting, commercial photography",
      "image_size": "square_hd",
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [Flux 2 Pro | Edit](../flux-2-pro-edit/) - Pro-tier image editing
- [Flux 2 | Flex](../flux-2-flex/) - Flexible generation with more controls
- [Flux 2](../flux-2/) - Standard Flux 2 generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
