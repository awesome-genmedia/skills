---
name: "Post Processing Parabolize"
description: "Apply a parabolize effect to images. Trigger: Use when the user wants to apply a parabolize tonal curve, or requests 'parabolize effect', 'parabolic tone curve', or 'post processing parabolize'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Parabolize

Apply a parabolic tonal curve to an image, creating unique contrast and tonal effects. Adjust the coefficient and vertex position for fine control.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-parabolize",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "parabolize_coeff": 1,
      "vertex_x": 0.5,
      "vertex_y": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `image_url` | string | (empty) | URL of image to process |
| `parabolize_coeff` | number | `1` | Parabolize coefficient |
| `vertex_x` | number | `0.5` | Vertex X position |
| `vertex_y` | number | `0.5` | Vertex Y position |

## Output

- **Type:** image

## Examples

### Subtle Parabolize
```json
{
  "model": "post-processing-parabolize",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/portrait.jpg",
    "parabolize_coeff": 0.8,
    "vertex_x": 0.5,
    "vertex_y": 0.4
  }
}
```

### Strong Tonal Effect
```json
{
  "model": "post-processing-parabolize",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/street-photo.jpg",
    "parabolize_coeff": 1.5,
    "vertex_x": 0.6,
    "vertex_y": 0.6
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Color Correction](../post-processing-color-correction/SKILL.md) - Brightness and contrast adjustments
- [Post Processing Dodge Burn](../post-processing-dodge-burn/SKILL.md) - Dodge and burn effects

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
