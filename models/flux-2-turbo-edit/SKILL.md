---
name: flux-2-turbo-edit
description: "Flux 2 | Turbo | Edit. Edit images with the fast Flux 2 Turbo model with prompt expansion. Triggers: image editing, flux turbo edit, fast edit, ai modify image"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Turbo | Edit

Edit images using the Flux 2 Turbo model with optional prompt expansion for enhanced results. Designed for fast, high-quality image modifications with configurable guidance scale.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-turbo-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add dramatic storm clouds to the sky",
      "image_urls": ["https://example.com/landscape.jpg"],
      "image_size": "square_hd",
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
| image_size | string | square_hd | The size of the image to generate. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_urls | array | - | The URLs of the images for editing. A maximum of 4 images are allowed. |
| num_images | integer | 1 | The number of images to generate. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to edit the image. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Quick edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-turbo-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Make the person wear a red hat",
      "image_urls": ["https://example.com/portrait.jpg"]
    }
  }'
```

**With prompt expansion and multiple outputs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-turbo-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Turn into cyberpunk style",
      "image_urls": ["https://example.com/city-street.jpg"],
      "enable_prompt_expansion": true,
      "guidance_scale": 3.5,
      "num_images": 2,
      "image_size": "landscape_16_9",
      "output_format": "webp",
      "seed": 42
    }
  }'
```

## Related Models

- [Flux 2 | Turbo | Text to Image](../flux-2-turbo-text-to-image/) - Generate images from text with Flux 2 Turbo
- [Flux 2 | Flash | Edit](../flux-2-flash-edit/) - Flash variant for even faster edits
- [Flux 2 | Max | Edit](../flux-2-max-edit/) - Maximum quality editing variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
