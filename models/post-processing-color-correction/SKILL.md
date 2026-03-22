---
name: "Post Processing Color Correction"
description: "Apply color correction adjustments to images. Trigger: Use when the user wants to adjust image colors, brightness, or contrast, or requests 'color correction', 'adjust brightness', 'fix colors', or 'post processing color'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Color Correction

Adjust brightness, contrast, saturation, gamma, and color temperature of images for precise color correction.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-color-correction",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "brightness": 0.1,
      "contrast": 0.2,
      "saturation": 0.1,
      "gamma": 1,
      "temperature": 0
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `brightness` | number | `0` | Brightness adjustment |
| `contrast` | number | `0` | Contrast adjustment |
| `gamma` | number | `1` | Gamma adjustment |
| `image_url` | string | (empty) | URL of image to process |
| `saturation` | number | `0` | Saturation adjustment |
| `temperature` | number | `0` | Color temperature adjustment |

## Output

- **Type:** image

## Examples

### Brighten and Warm
```json
{
  "model": "post-processing-color-correction",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/dark-photo.jpg",
    "brightness": 0.3,
    "contrast": 0.1,
    "temperature": 0.2,
    "gamma": 1.1
  }
}
```

### High Contrast Desaturated
```json
{
  "model": "post-processing-color-correction",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/landscape.jpg",
    "contrast": 0.4,
    "saturation": -0.3,
    "brightness": 0,
    "gamma": 0.9
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Color Tint](../post-processing-color-tint/SKILL.md) - Apply color tints
- [Post Processing Dodge Burn](../post-processing-dodge-burn/SKILL.md) - Dodge and burn effects

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
