---
name: bytedance-seedream-v4-5-edit
description: "Bytedance | Seedream | v4.5 | Edit. Edit images using text prompts with Bytedance Seedream. Triggers: image editing, seedream, bytedance, inpainting, photo edit"
allowed-tools: Bash(curl *), WebFetch
---

# Bytedance | Seedream | v4.5 | Edit

Edit existing images using text prompts with Bytedance's Seedream v4.5 model. Supports up to 10 input images and multi-image generation with configurable resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v4-5-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "change the background to a tropical beach at sunset",
      "image_urls": ["https://example.com/photo.jpg"],
      "image_size": "square_hd"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_safety_checker | boolean | true | Enable safety checker on generated outputs. |
| image_size | string | square_hd | Output image size. enum: square_hd, square, portrait_4_3, portrait_16_9, landscape_4_3, landscape_16_9, auto_2K, auto_4K |
| image_urls | array | | List of URLs of input images for editing. Up to 10 images supported. |
| max_images | integer | 1 | If set to a number greater than one, enables multi-image generation. |
| num_images | integer | 1 | Number of separate model generations to be run with the prompt. |
| prompt | string | | The text prompt used to edit the image. |
| seed | integer | | Random seed to control the stochasticity of image generation. |

## Examples

**Background replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v4-5-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "replace background with a modern office interior",
      "image_urls": ["https://example.com/portrait.jpg"],
      "image_size": "portrait_4_3",
      "num_images": 2
    }
  }'
```

**Style transformation on multiple images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-seedream-v4-5-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "convert to watercolor painting style with soft edges",
      "image_urls": ["https://example.com/image1.jpg", "https://example.com/image2.jpg"],
      "image_size": "auto_2K",
      "seed": 42
    }
  }'
```

## Related Models

- [Bytedance | Seedream | v4.5 | Text to Image](../bytedance-seedream-v4-5-text-to-image/) - Generate images from text
- [Flux 2 | Edit](../flux-2-edit/) - Alternative image editing model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
