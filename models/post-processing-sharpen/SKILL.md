---
name: "Post Processing Sharpen"
description: "Sharpen images with multiple sharpening modes. Trigger: Use when the user wants to sharpen an image, or requests 'sharpen image', 'make image sharper', or 'post processing sharpen'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Sharpen

Sharpen images using basic, smart, or CAS (Contrast Adaptive Sharpening) modes. Fine-tune the sharpness with radius, strength, and edge preservation controls.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-sharpen",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "sharpen_mode": "basic",
      "sharpen_alpha": 1,
      "sharpen_radius": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `cas_amount` | number | `0.8` | CAS sharpening amount |
| `image_url` | string | (empty) | URL of image to process |
| `noise_radius` | integer | `7` | Noise radius for smart sharpen |
| `preserve_edges` | number | `0.75` | Edge preservation factor |
| `sharpen_alpha` | number | `1` | Sharpen strength (for basic mode) |
| `sharpen_mode` | string | `basic` | Sharpening type. Options: `basic`, `smart`, `cas` |
| `sharpen_radius` | integer | `1` | Sharpen radius (for basic mode) |
| `smart_sharpen_ratio` | number | `0.5` | Smart sharpen blend ratio |
| `smart_sharpen_strength` | number | `5` | Smart sharpen strength |

## Output

- **Type:** image

## Examples

### Basic Sharpen
```json
{
  "model": "post-processing-sharpen",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/soft-photo.jpg",
    "sharpen_mode": "basic",
    "sharpen_alpha": 1.5,
    "sharpen_radius": 2
  }
}
```

### CAS Sharpening
```json
{
  "model": "post-processing-sharpen",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/landscape.jpg",
    "sharpen_mode": "cas",
    "cas_amount": 0.9
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Blur](../post-processing-blur/SKILL.md) - Blur effects for images
- [Post Processing Color Correction](../post-processing-color-correction/SKILL.md) - Color adjustments

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
