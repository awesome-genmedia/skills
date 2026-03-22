---
name: gpt-image-v1-5-text-to-image
description: "GPT Image | v1.5 | Text to Image. Generate images from text prompts using GPT Image v1.5. Triggers: gpt image, text to image, openai image, ai art generation"
allowed-tools: Bash(curl *), WebFetch
---

# GPT Image | v1.5 | Text to Image

Generate images from text prompts using GPT Image v1.5. Supports transparent backgrounds, configurable quality and moderation levels, and multiple output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gpt-image-v1-5-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic image of a golden retriever puppy sitting in a field of daisies, soft afternoon light",
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
| moderation | string | low | Content moderation level. Options: `low`, `auto` |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | png | Output format for the images. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt for image generation. |
| quality | string | high | Quality for the generated image. Options: `low`, `medium`, `high` |

## Examples

**Simple generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gpt-image-v1-5-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A modern logo design for a coffee brand called Brew & Co, minimalist style"
    }
  }'
```

**Product asset with transparent background:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gpt-image-v1-5-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A sleek wireless bluetooth speaker, product photography, white background",
      "background": "transparent",
      "image_size": "1024x1024",
      "quality": "high",
      "num_images": 3,
      "output_format": "png"
    }
  }'
```

**Wide landscape image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gpt-image-v1-5-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A panoramic view of the Grand Canyon at golden hour, dramatic clouds",
      "image_size": "1536x1024",
      "quality": "high",
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [GPT Image | v1.5 | Edit](../gpt-image-v1-5-edit/) - Edit images with GPT Image v1.5
- [P image | Text to Image](../p-image-text-to-image/) - Alternative text to image generation
- [Flux 2 | Max | Text to Image](../flux-2-max-text-to-image/) - Flux-based text to image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
