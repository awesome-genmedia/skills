---
name: luma-photon-reframe-image
description: "Luma Photon | Reframe Image. Reframe and extend images to different aspect ratios using Luma Photon AI. Triggers: luma, photon, reframe, extend image, outpainting, aspect ratio"
allowed-tools: Bash(curl *), WebFetch
---

# Luma Photon | Reframe Image

Reframe and extend images to different aspect ratios using Luma Photon AI. Supports precise coordinate-based reframing, grid positioning, and prompt-guided content generation for extended areas.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-photon-reframe-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait-photo.jpg",
      "aspect_ratio": "16:9",
      "prompt": "Extend the scene with a modern office background"
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

**Convert portrait to landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-photon-reframe-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/vertical-photo.jpg",
      "aspect_ratio": "21:9",
      "prompt": "Extend the scene naturally with matching environment on both sides"
    }
  }'
```

**Reframe to square with grid positioning:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "luma-photon-reframe-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape-photo.jpg",
      "aspect_ratio": "1:1",
      "grid_position_x": 50,
      "grid_position_y": 50
    }
  }'
```

## Related Models

- [luma-photon-flash-reframe-image](../luma-photon-flash-reframe-image/) - Flash (faster) reframe

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
