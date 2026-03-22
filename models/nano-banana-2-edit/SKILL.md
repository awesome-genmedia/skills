---
name: nano-banana-2-edit
description: "Nano Banana 2 | Edit. Edit images with text prompts at up to 4K resolution with multiple output formats. Triggers: image edit, nano banana, edit, modify image"
allowed-tools: Bash(curl *), WebFetch
---

# Nano Banana 2 | Edit

Edit images using text prompts with support for multiple aspect ratios, resolutions up to 4K, and various output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-2-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Make the background a tropical beach at sunset",
      "image_urls": ["https://example.com/portrait.jpg"],
      "aspect_ratio": "16:9",
      "resolution": "2K"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Aspect ratio of the generated image. enum: 1:1, 3:2, 2:3, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, 21:9 |
| image_urls | array | | URLs of images for image-to-image generation or editing. |
| limit_generations | boolean | true | Experimental parameter to limit generations from each processing round. |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | png | Output image format. enum: jpeg, png, webp |
| prompt | string | | The prompt for image editing. |
| resolution | string | 1K | Resolution of the generated image. enum: 1K, 2K, 4K |

## Examples

**Basic image edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-2-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add a futuristic cityscape in the background",
      "image_urls": ["https://example.com/photo.jpg"],
      "resolution": "2K",
      "output_format": "png"
    }
  }'
```

**Multiple output images at 4K:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-2-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Transform this photo into an oil painting style",
      "image_urls": ["https://example.com/landscape.jpg"],
      "num_images": 3,
      "resolution": "4K",
      "aspect_ratio": "16:9",
      "output_format": "jpeg"
    }
  }'
```

**Ultrawide edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-2-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Extend the scene to show a panoramic mountain view",
      "image_urls": ["https://example.com/mountains.jpg"],
      "aspect_ratio": "21:9",
      "resolution": "2K"
    }
  }'
```

## Related Models

- [nano-banana-2-text-to-image](../nano-banana-2-text-to-image/) - Nano Banana 2 text to image generation
- [firered-image-edit-v1-1](../firered-image-edit-v1-1/) - Firered image editing
- [xai-grok-imagine-image-edit](../xai-grok-imagine-image-edit/) - Grok image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
