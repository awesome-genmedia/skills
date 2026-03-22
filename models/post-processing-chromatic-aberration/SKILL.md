---
name: "Post Processing Chromatic Aberration"
description: "Apply chromatic aberration effects to images. Trigger: Use when the user wants to add chromatic aberration, or requests 'chromatic aberration', 'color fringing', 'RGB split', or 'post processing chromatic'."
allowed-tools: ["Bash"]
---

# Post Processing | Chromatic Abberation

Apply chromatic aberration by shifting individual RGB color channels horizontally or vertically, creating color fringing effects.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "post-processing-chromatic-aberration",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "red_shift": 3,
      "red_direction": "horizontal",
      "blue_shift": -3,
      "blue_direction": "horizontal",
      "green_shift": 0,
      "green_direction": "horizontal"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `blue_direction` | string | `horizontal` | Blue channel shift direction. Options: `horizontal`, `vertical` |
| `blue_shift` | integer | `0` | Blue channel shift amount |
| `green_direction` | string | `horizontal` | Green channel shift direction. Options: `horizontal`, `vertical` |
| `green_shift` | integer | `0` | Green channel shift amount |
| `image_url` | string | (empty) | URL of image to process |
| `red_direction` | string | `horizontal` | Red channel shift direction. Options: `horizontal`, `vertical` |
| `red_shift` | integer | `0` | Red channel shift amount |

## Output

- **Type:** image

## Examples

### Subtle Lens Effect
```json
{
  "model": "post-processing-chromatic-aberration",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/portrait.jpg",
    "red_shift": 2,
    "red_direction": "horizontal",
    "blue_shift": -2,
    "blue_direction": "horizontal"
  }
}
```

### Glitch Art Style
```json
{
  "model": "post-processing-chromatic-aberration",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/abstract.jpg",
    "red_shift": 8,
    "red_direction": "horizontal",
    "green_shift": -4,
    "green_direction": "vertical",
    "blue_shift": -8,
    "blue_direction": "horizontal"
  }
}
```

## Related Models

- [Post Processing Combine](../post-processing/SKILL.md) - Apply multiple effects at once
- [Post Processing Blur](../post-processing-blur/SKILL.md) - Apply blur effects
- [Post Processing Grain](../post-processing-grain/SKILL.md) - Add film grain

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
