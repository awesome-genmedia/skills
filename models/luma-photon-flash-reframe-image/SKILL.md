---
name: luma-photon-flash-reframe-image
description: "Luma Photon | Flash | Reframe Image. Quickly reframe and extend images to different aspect ratios using Luma Photon Flash. Triggers: luma, photon, flash, reframe, extend image, outpainting, fast"
allowed-tools: Bash(curl *), WebFetch
---

# Luma Photon | Flash | Reframe Image

Quickly reframe and extend images to different aspect ratios using Luma Photon Flash. Optimized for speed while supporting precise coordinate-based reframing and prompt-guided content generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-photon-flash-reframe-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-photo.jpg",
      "aspect_ratio": "16:9",
      "prompt": "Extend the scene with a clean studio background"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the reframed image. enum: 1:1, 16:9, 9:16, 4:3, 3:4, 21:9, 9:21 |
| grid_position_x | integer | | X position of the grid for reframing |
| grid_position_y | integer | | Y position of the grid for reframing |
| image_url | string | | URL of the input image to reframe |
| prompt | string | | Optional prompt for reframing |
| x_end | integer | | End X coordinate for reframing |
| x_start | integer | | Start X coordinate for reframing |
| y_end | integer | | End Y coordinate for reframing |
| y_start | integer | | Start Y coordinate for reframing |

## Examples

**Quick social media reformat:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-photon-flash-reframe-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/wide-photo.jpg",
      "aspect_ratio": "9:16",
      "prompt": "Extend vertically with sky above and ground below, matching the scene"
    }
  }'
```

**Ultrawide banner creation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-photon-flash-reframe-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/hero-image.jpg",
      "aspect_ratio": "21:9",
      "prompt": "Extend the background seamlessly to create a panoramic banner"
    }
  }'
```

## Related Models

- [luma-photon-reframe-image](../luma-photon-reframe-image/) - Standard quality reframe (higher quality)

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
