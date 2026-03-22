---
name: "Luma Dream Machine Reframe Image"
description: "Reframe and expand images using Luma Dream Machine. Trigger: Use when the user wants to reframe an image, expand image boundaries, or requests 'reframe image', 'outpaint', 'expand image', or 'luma reframe'."
allowed-tools: ["Bash"]
---

# Luma Dream Machine | Reframe Image

Reframe and expand images to new aspect ratios using Luma's Dream Machine. Place the original image within a larger canvas and generate the surrounding content.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "reframe-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "aspect_ratio": "16:9",
      "prompt": "Extend the scene to show a beautiful mountain landscape",
      "model": "photon-flash-1"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `16:9` | Target aspect ratio. Options: `1:1`, `3:4`, `4:3`, `9:16`, `16:9`, `9:21`, `21:9` |
| `grid_position_x` | integer | (empty) | X position of the input in the grid, in pixels. Controls horizontal positioning |
| `grid_position_y` | integer | (empty) | Y position of the input in the grid, in pixels. Controls vertical positioning |
| `image` | string | (empty) | The image to reframe (file upload) |
| `image_url` | string | (empty) | URL of the image to reframe |
| `model` | string | `photon-flash-1` | Model to use. Options: `photon-flash-1`, `photon-1` |
| `prompt` | string | (empty) | A prompt to guide the reframing generation |
| `x_end` | integer | (empty) | X end of crop bounds in pixels. Right boundary |
| `x_start` | integer | (empty) | X start of crop bounds in pixels. Left boundary |
| `y_end` | integer | (empty) | Y end of crop bounds in pixels. Bottom boundary |
| `y_start` | integer | (empty) | Y start of crop bounds in pixels. Top boundary |

## Output

- **Type:** image

## Examples

### Expand Portrait to Landscape
```json
{
  "model": "reframe-image",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/tight-portrait.jpg",
    "aspect_ratio": "16:9",
    "prompt": "Extend to show the full room environment with warm lighting",
    "model": "photon-1"
  }
}
```

### Ultra-Wide Panorama
```json
{
  "model": "reframe-image",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/landscape.jpg",
    "aspect_ratio": "21:9",
    "prompt": "Extend the panoramic mountain vista with rolling hills and clouds",
    "model": "photon-flash-1"
  }
}
```

### Square to Portrait
```json
{
  "model": "reframe-image",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/square-photo.jpg",
    "aspect_ratio": "9:16",
    "prompt": "Extend vertically to show the full building and sky above"
  }
}
```

## Related Models

- [Seedream V4 Edit](../seedream-v4-edit/SKILL.md) - General-purpose image editing
- [Nano Banana Edit](../nano-banana-edit/SKILL.md) - Fast image editing
- [Imagen 4 Preview](../imagen4-preview/SKILL.md) - Text-to-image generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
