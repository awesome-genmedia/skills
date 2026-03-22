---
name: gpt-image-v1-5-edit
description: "GPT Image | v1.5 | Edit. Edit images using GPT Image v1.5 with reference images and text prompts. Triggers: gpt image edit, image editing, ai edit, openai image"
allowed-tools: Bash(curl *), WebFetch
---

# GPT Image | v1.5 | Edit

Edit images using GPT Image v1.5. Supports reference images, transparent backgrounds, configurable moderation levels, and quality settings. Can generate multiple output images in various formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gpt-image-v1-5-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add a festive holiday wreath on the front door",
      "image_urls": ["https://example.com/house-front.jpg"],
      "image_size": "1024x1024",
      "quality": "high",
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| background | string | auto | Background for the generated image. Options: `auto`, `transparent`, `opaque` |
| image_size | string | 1024x1024 | Aspect ratio for the generated image. Options: `1024x1024`, `1536x1024`, `1024x1536` |
| image_urls | array | - | The URLs of the images to use as a reference for the generation. |
| input_fidelity | string | high | Input fidelity for the generated image. Options: `low`, `high` |
| moderation | string | low | Content moderation level. Options: `low`, `auto` |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | png | Output format for the images. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt for image generation. |
| quality | string | high | Quality for the generated image. Options: `low`, `medium`, `high` |

## Examples

**Simple edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gpt-image-v1-5-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the wall paint to a soft blue color",
      "image_urls": ["https://example.com/living-room.jpg"]
    }
  }'
```

**Transparent background edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gpt-image-v1-5-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Extract the product and place it on a clean transparent background",
      "image_urls": ["https://example.com/product-messy-bg.jpg"],
      "background": "transparent",
      "image_size": "1024x1024",
      "quality": "high",
      "num_images": 2,
      "output_format": "png"
    }
  }'
```

## Related Models

- [GPT Image | v1.5 | Text to Image](../gpt-image-v1-5-text-to-image/) - Generate images from text with GPT Image
- [P Image | Edit](../p-image-edit/) - Alternative AI image editing
- [Flux 2 | Max | Edit](../flux-2-max-edit/) - Flux-based image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
