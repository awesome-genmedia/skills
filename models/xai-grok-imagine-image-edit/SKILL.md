---
name: xai-grok-imagine-image-edit
description: "XAI | Grok | Imagine | Image Edit. Edit images with text prompts using xAI Grok Imagine. Triggers: image edit, grok, xai, edit image, modify"
allowed-tools: Bash(curl *), WebFetch
---

# XAI | Grok | Imagine | Image Edit

Edit existing images using text descriptions with xAI's Grok Imagine. Supports multiple output images and various output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Remove the background and replace it with a tropical beach",
      "image_url": "https://example.com/portrait.jpg",
      "num_images": 1,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | | URL of the image to edit. |
| num_images | integer | 1 | Number of images to generate. |
| output_format | string | jpeg | Output format. enum: jpeg, png, webp |
| prompt | string | | Text description of the desired edit. |

## Examples

**Background replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Replace the background with a futuristic sci-fi cityscape",
      "image_url": "https://example.com/person-standing.jpg",
      "num_images": 2,
      "output_format": "png"
    }
  }'
```

**Object modification:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "xai-grok-imagine-image-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the car color from blue to red",
      "image_url": "https://example.com/blue-car.jpg",
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [xai-grok-imagine-text-to-image](../xai-grok-imagine-text-to-image/) - Grok text to image
- [xai-grok-imagine-edit-video](../xai-grok-imagine-edit-video/) - Grok video editing
- [firered-image-edit-v1-1](../firered-image-edit-v1-1/) - Firered image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
