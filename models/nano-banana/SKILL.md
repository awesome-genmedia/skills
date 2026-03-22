---
name: "Nano Banana"
description: "Fast image generation using Nano Banana. Trigger: Use when the user wants to quickly generate images, or requests 'nano banana', 'fast image generation', or 'quick image create'."
allowed-tools: ["Bash"]
---

# Nano Banana

Generate images quickly with Nano Banana. Supports multiple aspect ratios and output formats with a streamlined parameter set.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy cabin in the woods during winter with snow on the roof",
      "aspect_ratio": "16:9",
      "num_images": 1,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `1:1` | Output aspect ratio. Options: `21:9`, `1:1`, `4:3`, `3:2`, `2:3`, `5:4`, `4:5`, `3:4`, `16:9`, `9:16` |
| `limit_generations` | boolean | `true` | Experimental parameter to limit generations per processing round |
| `num_images` | integer | `1` | Number of images to generate |
| `output_format` | string | `png` | Output format. Options: `jpeg`, `png` |
| `prompt` | string | `false` | Text prompt for image generation |

## Output

- **Type:** array

## Examples

### Square Social Media Post
```json
{
  "model": "nano-banana",
  "version": "0.0.1",
  "input": {
    "prompt": "A flat-lay arrangement of coffee, notebook, and flowers on a wooden table",
    "aspect_ratio": "1:1",
    "num_images": 1,
    "output_format": "jpeg"
  }
}
```

### Widescreen Wallpaper
```json
{
  "model": "nano-banana",
  "version": "0.0.1",
  "input": {
    "prompt": "A futuristic space station orbiting a gas giant planet with rings",
    "aspect_ratio": "21:9",
    "num_images": 2,
    "output_format": "png"
  }
}
```

## Related Models

- [Nano Banana Edit](../nano-banana-edit/SKILL.md) - Edit images with Nano Banana
- [Seedream V4 Text to Image](../seedream-v4-text-to-image/SKILL.md) - Higher-quality text-to-image
- [Imagen 4 Preview](../imagen4-preview/SKILL.md) - Google's image generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
