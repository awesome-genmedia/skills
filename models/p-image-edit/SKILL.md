---
name: p-image-edit
description: "P Image | Edit. Edit images with AI using reference images and text prompts. Triggers: image editing, ai edit, photo edit, p image"
allowed-tools: Bash(curl *), WebFetch
---

# P Image | Edit

Edit images using AI with text prompts and reference images. Supports various aspect ratios, turbo mode for faster processing, and reproducible generation with seed control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the dress color to emerald green",
      "images": ["https://example.com/fashion-photo.jpg"],
      "aspect_ratio": "match_input_image",
      "turbo": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | match_input_image | Aspect ratio of the output. Options: `match_input_image`, `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3` |
| disable_safety_checker | boolean | false | Disable safety checker for generated images. |
| images | array | - | Images to use as a reference. For editing, provide the main image as the first. |
| prompt | string | - | Text prompt for image generation. Describe your edit task clearly. |
| seed | integer | - | Random seed. Set for reproducible generation. |
| turbo | boolean | true | If turned on, the model will run faster with additional optimizations. |

## Examples

**Basic edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Remove the text overlay and clean up the background",
      "images": ["https://example.com/photo-with-text.jpg"]
    }
  }'
```

**Edit with specific aspect ratio and seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform the scene into a snowy winter landscape with frost on the trees",
      "images": ["https://example.com/autumn-park.jpg"],
      "aspect_ratio": "16:9",
      "turbo": false,
      "seed": 42
    }
  }'
```

## Related Models

- [P image | Text to Image](../p-image-text-to-image/) - Generate images from text with P Image
- [Flux 2 | Turbo | Edit](../flux-2-turbo-edit/) - Flux-based image editing
- [GPT Image | v1.5 | Edit](../gpt-image-v1-5-edit/) - GPT-powered image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
