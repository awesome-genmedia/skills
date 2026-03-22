---
name: flux-2-flash-text-to-image
description: "Flux 2 | Flash | Text to Image. Generate images ultra-fast from text prompts with Flux 2 Flash. Triggers: text to image, fast generation, flux flash, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Flash | Text to Image

Generate images from text prompts using the ultra-fast Flux 2 Flash model. Optimized for the fastest possible generation with optional prompt expansion and configurable guidance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flash-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A whimsical treehouse nestled in an ancient oak tree, fairy lights and rope bridges",
      "image_size": "landscape_4_3",
      "guidance_scale": 2.5,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| enable_prompt_expansion | boolean | false | If set to true, the prompt will be expanded for better results. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| guidance_scale | number | 2.5 | Guidance scale for how closely the model follows the prompt. |
| image_size | string | landscape_4_3 | The size of the image to generate. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| num_images | integer | 1 | The number of images to generate. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to generate an image from. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Quick generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flash-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A sleek electric car concept design, studio lighting"
    }
  }'
```

**Batch generation with prompt expansion:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flash-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Cute robot character",
      "enable_prompt_expansion": true,
      "num_images": 3,
      "image_size": "square_hd",
      "guidance_scale": 3.0,
      "output_format": "webp",
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Flash | Edit](../flux-2-flash-edit/) - Edit images with Flux 2 Flash
- [Flux 2 | Turbo | Text to Image](../flux-2-turbo-text-to-image/) - Turbo variant for generation
- [Flux 2 | Max | Text to Image](../flux-2-max-text-to-image/) - Maximum quality generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
