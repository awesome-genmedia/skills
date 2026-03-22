---
name: "Post Processing Vignette"
description: "Apply a vignette effect to images. Trigger: Use when the user wants to add a vignette to an image, or requests 'vignette effect', 'darken edges', or 'post processing vignette'."
allowed-tools: ["Bash"]
---

# Post Proccessing | Vignette

Apply a vignette effect to images, darkening the edges to draw focus to the center of the frame.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-vignette",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "vignette_strength": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `image_url` | string | (empty) | URL of image to process |
| `vignette_strength` | number | `0.5` | Vignette strength |

## Output

- **Type:** image

## Examples

### Subtle Vignette
```json
{
  "model": "post-processing-vignette",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/portrait.jpg",
    "vignette_strength": 0.3
  }
}
```

### Strong Dramatic Vignette
```json
{
  "model": "post-processing-vignette",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/landscape.jpg",
    "vignette_strength": 0.8
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Color Correction](../post-processing-color-correction/SKILL.md) - Adjust brightness, contrast, and more
- [Post Processing Grain](../post-processing-grain/SKILL.md) - Add film grain effect

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
