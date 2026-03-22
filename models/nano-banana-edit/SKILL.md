---
name: "Nano Banana Edit"
description: "Edit images using Nano Banana. Trigger: Use when the user wants to edit images with Nano Banana, or requests 'nano banana edit', 'quick image edit', or 'fast AI image editing'."
allowed-tools: ["Bash"]
---

# Nano Banana | Edit

Edit existing images using text prompts with Nano Banana. Supports multiple aspect ratios including automatic detection from the input image.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "nano-banana-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the sky to a dramatic sunset with orange and purple clouds",
      "image_urls": ["https://example.com/landscape.jpg"],
      "aspect_ratio": "auto",
      "num_images": 1,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `1:1` | Aspect ratio. Options: `21:9`, `1:1`, `4:3`, `3:2`, `2:3`, `5:4`, `4:5`, `3:4`, `16:9`, `9:16`, `auto` |
| `image_urls` | array | `false` | URLs of images to edit |
| `limit_generations` | boolean | `true` | Experimental parameter to limit generations per processing round |
| `num_images` | integer | `1` | Number of images to generate |
| `output_format` | string | `jpeg` | Output format. Options: `jpeg`, `png` |
| `prompt` | string | `false` | Text prompt for image editing |

## Output

- **Type:** array

## Examples

### Background Change
```json
{
  "model": "nano-banana-edit",
  "version": "0.0.1",
  "input": {
    "prompt": "Replace the background with a futuristic cityscape at night",
    "image_urls": ["https://example.com/portrait.jpg"],
    "aspect_ratio": "auto",
    "output_format": "png"
  }
}
```

### Style Modification
```json
{
  "model": "nano-banana-edit",
  "version": "0.0.1",
  "input": {
    "prompt": "Transform into a watercolor painting style",
    "image_urls": ["https://example.com/photo.jpg"],
    "aspect_ratio": "4:3",
    "num_images": 2,
    "output_format": "jpeg"
  }
}
```

## Related Models

- [Nano Banana](../nano-banana/SKILL.md) - Text-to-image generation
- [Seedream V4 Edit](../seedream-v4-edit/SKILL.md) - Advanced image editing
- [Flux Krea Image to Image](../flux-krea-image-to-image/SKILL.md) - Image transformation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
