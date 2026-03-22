---
name: flux-2-turbo-text-to-image
description: "Flux 2 | Turbo | Text to Image. Generate images fast from text prompts with Flux 2 Turbo. Triggers: text to image, fast image generation, flux turbo, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Turbo | Text to Image

Generate images from text prompts using the Flux 2 Turbo model. Optimized for speed with optional prompt expansion and configurable guidance for balanced quality and performance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-turbo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A vibrant underwater coral reef teeming with tropical fish, sunlight filtering through the water",
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
    "model": "flux-2-turbo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A modern minimalist kitchen with marble countertops and pendant lighting"
    }
  }'
```

**Enhanced generation with prompt expansion:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-turbo-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Astronaut on Mars",
      "enable_prompt_expansion": true,
      "guidance_scale": 3.0,
      "num_images": 2,
      "image_size": "square_hd",
      "output_format": "webp",
      "seed": 9999
    }
  }'
```

## Related Models

- [Flux 2 | Turbo | Edit](../flux-2-turbo-edit/) - Edit images with Flux 2 Turbo
- [Flux 2 | Flash | Text to Image](../flux-2-flash-text-to-image/) - Flash variant for quick generation
- [Flux 2 | Max | Text to Image](../flux-2-max-text-to-image/) - Maximum quality generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
