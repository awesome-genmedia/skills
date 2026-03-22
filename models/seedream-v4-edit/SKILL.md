---
name: "Seedream V4 Edit"
description: "Edit images using Seedream V4 with text prompts. Trigger: Use when the user wants to edit an existing image with AI, or requests 'seedream edit', 'AI image editing', or 'edit my image with text'."
allowed-tools: ["Bash"]
---

# Seedream V4 | Edit

Edit images using text prompts. Provide one or more input images along with editing instructions to transform, modify, or enhance them.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedream-v4-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Change the background to a tropical beach at sunset",
      "image_urls": ["https://example.com/photo.jpg"],
      "image_size": "square_hd",
      "num_images": 1,
      "enable_safety_checker": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `enable_safety_checker` | boolean | `true` | If set to true, the safety checker will be enabled |
| `image_size` | string | `square_hd` | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9`, `auto`, `auto_2K`, `auto_4K` |
| `image_urls` | array | (empty) | List of URLs of input images for editing |
| `num_images` | integer | `1` | Number of times to retry generation with the prompt |
| `prompt` | string | (empty) | The text prompt used to edit the image |
| `seed` | integer | (empty) | Random seed to control the stochasticity of image generation |

## Output

- **Type:** array

## Examples

### Background Replacement
```json
{
  "model": "seedream-v4-edit",
  "version": "0.0.1",
  "input": {
    "prompt": "Replace the background with a snowy mountain landscape",
    "image_urls": ["https://example.com/portrait.jpg"],
    "image_size": "portrait_4_3",
    "num_images": 1
  }
}
```

### Style Transfer Edit
```json
{
  "model": "seedream-v4-edit",
  "version": "0.0.1",
  "input": {
    "prompt": "Make it look like a watercolor painting with soft brushstrokes",
    "image_urls": ["https://example.com/landscape.jpg"],
    "image_size": "landscape_4_3",
    "num_images": 2,
    "seed": 42
  }
}
```

## Related Models

- [Seedream V4 Text to Image](../seedream-v4-text-to-image/SKILL.md) - Generate images from text
- [Nano Banana Edit](../nano-banana-edit/SKILL.md) - Alternative image editing model
- [Flux Krea Image to Image](../flux-krea-image-to-image/SKILL.md) - Image-to-image transformation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
