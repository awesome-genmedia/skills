---
name: flux-2-flash-edit
description: "Flux 2 | Flash | Edit. Edit images with the ultra-fast Flux 2 Flash model. Triggers: image editing, flux flash edit, fast edit, quick edit"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Flash | Edit

Edit images using the ultra-fast Flux 2 Flash model with optional prompt expansion. Designed for rapid iteration on image edits with configurable guidance and output options.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flash-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Replace the sky with northern lights",
      "image_urls": ["https://example.com/night-scene.jpg"],
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
    "model": "flux-2-flash-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add a cute kitten sitting on the table",
      "image_urls": ["https://example.com/desk.jpg"]
    }
  }'
```

**Enhanced edit with prompt expansion:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-flash-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Make it look like a vintage photograph",
      "image_urls": ["https://example.com/modern-photo.jpg"],
      "enable_prompt_expansion": true,
      "guidance_scale": 3.0,
      "num_images": 2,
      "output_format": "jpeg",
      "seed": 777
    }
  }'
```

## Related Models

- [Flux 2 | Flash | Text to Image](../flux-2-flash-text-to-image/) - Generate images from text with Flux 2 Flash
- [Flux 2 | Turbo | Edit](../flux-2-turbo-edit/) - Turbo variant for editing
- [Flux 2 | Max | Edit](../flux-2-max-edit/) - Maximum quality editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
