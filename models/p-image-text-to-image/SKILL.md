---
name: p-image-text-to-image
description: "P image | Text to Image. Generate images from text prompts with custom aspect ratios. Triggers: text to image, image generation, p image, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# P image | Text to Image

Generate images from text prompts using the P Image model. Supports various preset aspect ratios and custom dimensions, with optional prompt upsampling for enhanced results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic eagle soaring over snow-capped mountains at golden hour, photorealistic",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the generated image. Options: `1:1`, `16:9`, `9:16`, `4:3`, `3:4`, `3:2`, `2:3`, `custom` |
| disable_safety_checker | boolean | false | Disable safety checker for generated images. |
| height | integer | - | Height of the generated image. Only used when aspect_ratio=custom. Must be a multiple of a specific value. |
| prompt | string | - | Text prompt for image generation. |
| prompt_upsampling | boolean | false | Upsample the prompt with an LLM for enhanced results. |
| seed | integer | - | Random seed. Set for reproducible generation. |
| width | integer | - | Width of the generated image. Only used when aspect_ratio=custom. Must be a multiple of a specific value. |

## Examples

**Simple generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cozy log cabin in the woods during autumn, smoke rising from the chimney"
    }
  }'
```

**Custom dimensions with prompt upsampling:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Futuristic spaceship interior",
      "aspect_ratio": "custom",
      "width": 1920,
      "height": 1080,
      "prompt_upsampling": true,
      "seed": 2024
    }
  }'
```

**Portrait format:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "p-image-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Elegant fashion portrait, studio lighting, minimalist background",
      "aspect_ratio": "9:16",
      "seed": 777
    }
  }'
```

## Related Models

- [P Image | Edit](../p-image-edit/) - Edit existing images with P Image
- [Flux 2 | Turbo | Text to Image](../flux-2-turbo-text-to-image/) - Flux-based text to image
- [GPT Image | v1.5 | Text to Image](../gpt-image-v1-5-text-to-image/) - GPT-powered image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
