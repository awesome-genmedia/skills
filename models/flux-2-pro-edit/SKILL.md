---
name: flux-2-pro-edit
description: "Flux 2 Pro | Edit. Professional-grade image editing with text prompts. Triggers: image editing, flux, pro, photo edit, professional"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 Pro | Edit

Professional-grade image editing using text prompts with Flux 2 Pro. Streamlined parameter set focused on quality output with configurable safety tolerance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-pro-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "remove the person in the background, fill with natural scenery",
      "image_urls": ["https://example.com/photo.jpg"],
      "image_size": "auto"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| image_size | string | auto | The size of the generated image. enum: auto, square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| image_urls | array | | List of URLs of input images for editing. |
| output_format | string | jpeg | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate an image from. |
| safety_tolerance | string | 2 | The safety tolerance level. 1 is most strict, 5 is most permissive. enum: 1, 2, 3, 4, 5 |
| seed | integer | | The seed to use for the generation. |

## Examples

**Object removal:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-pro-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "remove the parked car from the driveway, fill with grass",
      "image_urls": ["https://example.com/house.jpg"],
      "image_size": "landscape_4_3",
      "output_format": "png"
    }
  }'
```

**Color grading edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-pro-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "apply warm golden hour color grading, enhance contrast",
      "image_urls": ["https://example.com/cityscape.jpg"],
      "image_size": "auto",
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 Pro](../flux-2-pro/) - Text-to-image generation with Pro quality
- [Flux 2 | Flex | Edit](../flux-2-flex-edit/) - Flexible image editing with more controls
- [Flux 2 | Edit](../flux-2-edit/) - Standard Flux 2 editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
