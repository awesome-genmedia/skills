---
name: nano-banana-pro-edit
description: "Nano Banana Pro | Edit. Edit images with up to 4K resolution and multiple aspect ratios. Triggers: image editing, nano banana, photo edit, inpainting"
allowed-tools: Bash(curl *), WebFetch
---

# Nano Banana Pro | Edit

Edit images with Nano Banana Pro. Supports multiple aspect ratios, up to 4K resolution, and batch generation with an experimental generation limiter.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-pro-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "add colorful graffiti art to the wall",
      "image_urls": ["https://example.com/wall.jpg"],
      "aspect_ratio": "16:9",
      "resolution": "1K"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | The aspect ratio of the generated image. enum: auto, 21:9, 16:9, 3:2, 4:3, 5:4, 1:1, 4:5, 3:4, 2:3, 9:16 |
| image_urls | array | | The URLs of the images for editing. |
| limit_generations | boolean | false | Experimental parameter to limit the number of generations per round. |
| num_images | integer | 1 | The number of images to generate. |
| output_format | string | png | The format of the generated image. enum: jpeg, png, webp |
| prompt | string | | The prompt for image editing. |
| resolution | string | 1K | The resolution of the image to generate. enum: 1K, 2K, 4K |

## Examples

**High-res style transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-pro-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "transform into Studio Ghibli animation style, dreamy atmosphere",
      "image_urls": ["https://example.com/countryside.jpg"],
      "aspect_ratio": "16:9",
      "resolution": "2K",
      "output_format": "png"
    }
  }'
```

**Batch editing with auto aspect:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-pro-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "add soft bokeh lights in the background",
      "image_urls": ["https://example.com/portrait.jpg"],
      "aspect_ratio": "auto",
      "num_images": 3,
      "resolution": "1K"
    }
  }'
```

## Related Models

- [Nano Banana Pro](../nano-banana-pro/) - Text-to-image generation
- [Gemini 3 Pro | Image Edit](../gemini-3-pro-image-preview-edit/) - Alternative editing model

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
