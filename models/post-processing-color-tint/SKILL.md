---
name: "Post Processing Color Tint"
description: "Apply color tints to images. Trigger: Use when the user wants to add a color tint, or requests 'color tint', 'sepia tone', 'vintage tint', or 'post processing tint'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Color Tint

Apply color tints to images with a wide selection of preset colors and adjustable strength.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-color-tint",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "tint_mode": "vintage",
      "tint_strength": 0.7
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `image_url` | string | (empty) | URL of image to process |
| `tint_mode` | string | `vintage` | Tint color. Options: `sepia`, `red`, `green`, `blue`, `cyan`, `magenta`, `yellow`, `purple`, `orange`, `warm`, `cool`, `lime`, `navy`, `vintage`, `rose`, `teal`, `maroon`, `peach`, `lavender`, `olive` |
| `tint_strength` | number | `1` | Tint strength |

## Output

- **Type:** image

## Examples

### Vintage Sepia
```json
{
  "model": "post-processing-color-tint",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/old-building.jpg",
    "tint_mode": "sepia",
    "tint_strength": 0.8
  }
}
```

### Cool Blue Tint
```json
{
  "model": "post-processing-color-tint",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/night-scene.jpg",
    "tint_mode": "cool",
    "tint_strength": 0.5
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Color Correction](../post-processing-color-correction/SKILL.md) - Adjust brightness, contrast, and temperature
- [Post Processing Grain](../post-processing-grain/SKILL.md) - Add film grain

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
