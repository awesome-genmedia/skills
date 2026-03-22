---
name: flux-2-flex-edit
description: "Flux 2 | Flex | Edit. Edit images with flexible guidance scale and prompt expansion. Triggers: image editing, flux, flex, photo edit, inpainting"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Flex | Edit

Edit images using text prompts with Flux 2 Flex. Features flexible guidance scale control, prompt expansion, and configurable safety tolerance levels.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flex-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "add a dramatic sunset sky in the background",
      "image_urls": ["https://example.com/photo.jpg"],
      "guidance_scale": 3.5,
      "image_size": "auto"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_prompt_expansion | boolean | true | Whether to expand the prompt using the model's own knowledge. |
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| guidance_scale | number | 3.5 | The guidance scale to use for the generation. |
| image_size | string | auto | The size of the generated image. enum: auto, square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9 |
| image_urls | array | | List of URLs of input images for editing. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | jpeg | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt to generate an image from. |
| safety_tolerance | string | 2 | The safety tolerance level. 1 is most strict, 5 is most permissive. enum: 1, 2, 3, 4, 5 |
| seed | integer | | The seed to use for the generation. |

## Examples

**Background replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flex-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "replace the background with a tropical beach at sunset",
      "image_urls": ["https://example.com/portrait.jpg"],
      "guidance_scale": 4.0,
      "image_size": "portrait_4_3",
      "output_format": "png",
      "num_inference_steps": 30
    }
  }'
```

**Style modification with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flex-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "convert to watercolor painting, soft brush strokes",
      "image_urls": ["https://example.com/landscape.jpg"],
      "guidance_scale": 5.0,
      "enable_prompt_expansion": false,
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Flex](../flux-2-flex/) - Text-to-image generation with Flex
- [Flux 2 Pro | Edit](../flux-2-pro-edit/) - Pro-tier image editing
- [Flux 2 | Edit](../flux-2-edit/) - Standard Flux 2 editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
