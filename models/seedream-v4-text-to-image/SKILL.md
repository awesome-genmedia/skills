---
name: "Seedream V4 Text to Image"
description: "Generate images from text using Seedream V4. Trigger: Use when the user wants to create an image from a description, or requests 'seedream', 'seedream text to image', or 'generate image with seedream'."
allowed-tools: ["Bash"]
---

# Seedream V4 | Text to Image

Generate high-quality images from text descriptions. Supports multiple output sizes and batch generation.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedream-v4-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with a koi pond and cherry blossom trees",
      "image_size": "landscape_4_3",
      "num_images": 1,
      "enable_safety_checker": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `enable_safety_checker` | boolean | `true` | If set to true, the safety checker will be enabled |
| `image_size` | string | `square_hd` | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| `num_images` | integer | `1` | Number of times to retry generation with the prompt |
| `prompt` | string | (empty) | The text prompt used to generate the image |
| `seed` | integer | (empty) | Random seed to control the stochasticity of image generation |

## Output

- **Type:** array

## Examples

### Landscape Photo
```json
{
  "model": "seedream-v4-text-to-image",
  "version": "0.0.1",
  "input": {
    "prompt": "A dramatic mountain landscape at golden hour with fog rolling through valleys",
    "image_size": "landscape_16_9",
    "num_images": 1
  }
}
```

### Character Illustration
```json
{
  "model": "seedream-v4-text-to-image",
  "version": "0.0.1",
  "input": {
    "prompt": "A fantasy warrior in ornate silver armor standing in a mystical forest",
    "image_size": "portrait_4_3",
    "num_images": 2,
    "seed": 99
  }
}
```

## Related Models

- [Seedream V4 Edit](../seedream-v4-edit/SKILL.md) - Edit existing images with text prompts
- [Imagen 4 Preview](../imagen4-preview/SKILL.md) - Google's image generation model
- [Nano Banana](../nano-banana/SKILL.md) - Fast image generation

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
