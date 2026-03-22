---
name: gemini-3-pro-image-preview-edit
description: "Gemini 3 Pro | Image Edit. Edit images using Google Gemini with multiple resolution options. Triggers: image editing, gemini, google, photo edit"
allowed-tools: Bash(curl *), WebFetch
---

# Gemini 3 Pro | Image Edit

Edit images using Google's Gemini 3 Pro model. Supports multiple aspect ratios, resolution up to 4K, and batch generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gemini-3-pro-image-preview-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "make the sky more dramatic with storm clouds",
      "image_urls": ["https://example.com/landscape.jpg"],
      "aspect_ratio": "16:9",
      "resolution": "1K"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | The aspect ratio of the generated image. enum: 21:9, 16:9, 3:2, 4:3, 5:4, 1:1, 4:5, 3:4, 2:3, 9:16 |
| image_urls | array | | The URLs of the images for editing. |
| num_images | integer | 1 | The number of images to generate. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt for image editing. |
| resolution | string | 1K | The resolution of the image to generate. enum: 1K, 2K, 4K |

## Examples

**High-res background replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gemini-3-pro-image-preview-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "replace the background with a modern art gallery, white walls",
      "image_urls": ["https://example.com/portrait.jpg"],
      "aspect_ratio": "3:4",
      "resolution": "2K",
      "output_format": "png"
    }
  }'
```

**Batch style edits:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gemini-3-pro-image-preview-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "convert to pencil sketch style, detailed cross-hatching",
      "image_urls": ["https://example.com/photo.jpg"],
      "num_images": 3,
      "resolution": "1K"
    }
  }'
```

## Related Models

- [Gemini 3 | Pro | Image Preview](../gemini-3-pro-image-preview/) - Text-to-image generation
- [Nano Banana Pro | Edit](../nano-banana-pro-edit/) - Alternative image editing model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
