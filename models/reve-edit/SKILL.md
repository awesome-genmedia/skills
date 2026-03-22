---
name: reve-edit
description: "Reve | Edit. Edit images with text-based instructions using the Reve model. Triggers: reve, edit image, image edit, reve edit, photo editing"
allowed-tools: Bash(curl *), WebFetch
---

# Reve | Edit

Edit images with text-based instructions using the Reve model. Provide a reference image and describe the desired changes to produce high-quality edited results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-edit",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/room-photo.jpg",
      "prompt": "Change the wall color to a warm terracotta and add potted plants on the windowsill",
      "num_images": 1,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| image_url | string | | URL of the reference image to edit |
| num_images | integer | 1 | Number of images to generate |
| output_format | string | png | Output format. enum: png, jpeg, webp |
| prompt | string | | Text description of how to edit the provided image |

## Examples

**Object removal:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-edit",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/street-photo.jpg",
      "prompt": "Remove the parked cars from the street and replace with a clean sidewalk",
      "output_format": "jpeg"
    }
  }'
```

**Style transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reve-edit",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/daytime-city.jpg",
      "prompt": "Transform this daytime scene into a dramatic nighttime scene with city lights glowing",
      "num_images": 2,
      "output_format": "png"
    }
  }'
```

## Related Models

- [reve-text-to-image](../reve-text-to-image/) - Generate images from text
- [reve-remix](../reve-remix/) - Remix reference images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
