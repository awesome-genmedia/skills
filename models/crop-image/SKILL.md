---
name: crop-image
description: "Crop Image. Crop images by percentage-based coordinates. Triggers: crop image, trim image, resize image, cut image"
allowed-tools: Bash(curl *), WebFetch
---

# Crop Image

Crop images using percentage-based coordinates and dimensions. Specify the crop region as percentages of the original image width and height for easy, resolution-independent cropping.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "crop-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "x_percent": 25,
      "y_percent": 16,
      "width_percent": 50,
      "height_percent": 50,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| height_percent | number | 100 | Height as percentage of image height (0-100). |
| image_url | string | - | The URL of the image to crop. Max file size: 9.5MB. |
| output_format | string | png | Output format for the cropped image. Options: `png`, `jpg`, `jpeg`, `webp` |
| width_percent | number | 100 | Width as percentage of image width (0-100). |
| x_percent | number | 25 | X coordinate as percentage of image width (0-100). |
| y_percent | number | 16 | Y coordinate as percentage of image height (0-100). |

## Examples

**Center crop to 50%:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "crop-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "x_percent": 25,
      "y_percent": 25,
      "width_percent": 50,
      "height_percent": 50
    }
  }'
```

**Crop top-left quadrant:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "crop-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/group-photo.jpg",
      "x_percent": 0,
      "y_percent": 0,
      "width_percent": 50,
      "height_percent": 50,
      "output_format": "jpeg"
    }
  }'
```

## Related Models

- [Rembg](../rembg/) - Remove image backgrounds
- [Each Upscaler](../each-upscaler/) - Upscale image resolution

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
