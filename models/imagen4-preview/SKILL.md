---
name: "Imagen 4 Preview"
description: "Generate images using Google Imagen 4 Preview. Trigger: Use when the user wants to create images with Imagen, or requests 'imagen 4', 'google image generation', or 'imagen preview'."
allowed-tools: ["Bash"]
---

# Imagen 4 | Preview

Generate images using Google's Imagen 4 model. Supports multiple aspect ratios, batch generation, and negative prompts for fine control.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "imagen4-preview",
    "version": "0.0.1",
    "input": {
      "prompt": "A photorealistic image of a golden retriever puppy playing in autumn leaves",
      "aspect_ratio": "4:3",
      "num_images": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `1:1` | Aspect ratio. Options: `1:1`, `16:9`, `9:16`, `3:4`, `4:3` |
| `negative_prompt` | string | (empty) | A description of what to discourage in the generated images |
| `num_images` | integer | `1` | Number of images to generate (1-4) |
| `prompt` | string | (empty) | The text prompt describing what you want to see |
| `seed` | string | (empty) | Random seed for reproducible generation |

## Output

- **Type:** image

## Examples

### Product Visualization
```json
{
  "model": "imagen4-preview",
  "version": "0.0.1",
  "input": {
    "prompt": "A minimalist glass perfume bottle on a white marble surface with soft shadows",
    "aspect_ratio": "1:1",
    "num_images": 2,
    "negative_prompt": "blurry, low quality, text, watermark"
  }
}
```

### Landscape Photography
```json
{
  "model": "imagen4-preview",
  "version": "0.0.1",
  "input": {
    "prompt": "Aerial view of turquoise ocean waves crashing on a white sand beach, high detail",
    "aspect_ratio": "16:9",
    "num_images": 1,
    "seed": "12345"
  }
}
```

### Portrait
```json
{
  "model": "imagen4-preview",
  "version": "0.0.1",
  "input": {
    "prompt": "A close-up portrait of an elderly craftsman with weathered hands working on pottery",
    "aspect_ratio": "3:4",
    "num_images": 1
  }
}
```

## Related Models

- [Seedream V4 Text to Image](../seedream-v4-text-to-image/SKILL.md) - ByteDance's text-to-image model
- [Ideogram Character](../ideogram-character/SKILL.md) - Character-consistent image generation
- [Nano Banana](../nano-banana/SKILL.md) - Fast image generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
