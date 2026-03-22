---
name: flux-2-klein-9b-base-edit
description: "Flux 2 | Klein | 9B | Base | Edit. Edit images using AI with the Flux 2 Klein 9B model. Triggers: image editing, flux edit, ai image edit, modify image"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Klein | 9B | Base | Edit

Edit images using AI-powered instructions with the Flux 2 Klein 9B Base model. Provide one or more images and a text prompt describing the desired edits, and the model generates modified versions.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Make the sky a vibrant sunset with orange and pink hues",
      "image_urls": ["https://example.com/landscape.jpg"],
      "image_size": "landscape_4_3",
      "num_inference_steps": 28,
      "guidance_scale": 5,
      "output_format": "png"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | regular | The acceleration level to use for image generation. Options: `none`, `regular`, `high` |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| guidance_scale | number | 5 | Guidance scale for classifier-free guidance. |
| image_size | string | landscape_4_3 | The size of the generated image. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| image_urls | array | - | The URLs of the images for editing. A maximum of 4 images are allowed. |
| negative_prompt | string | - | Negative prompt for classifier-free guidance. Describes what to avoid in the image. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to edit the image. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Basic image edit:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Replace the background with a tropical beach",
      "image_urls": ["https://example.com/portrait.jpg"],
      "num_images": 1
    }
  }'
```

**High-quality edit with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Add a golden retriever sitting next to the person",
      "image_urls": ["https://example.com/park-photo.jpg"],
      "negative_prompt": "blurry, distorted, low quality",
      "guidance_scale": 7,
      "num_inference_steps": 35,
      "output_format": "jpeg",
      "seed": 42
    }
  }'
```

**Multiple images with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-edit",
    "version": "0.0.1",
    "input": {
      "prompt": "Apply a watercolor painting style",
      "image_urls": ["https://example.com/photo1.jpg", "https://example.com/photo2.jpg"],
      "acceleration": "high",
      "num_images": 2,
      "image_size": "square_hd"
    }
  }'
```

## Related Models

- [Flux 2 | Klein | 9B | Base | Text to Image](../flux-2-klein-9b-base-text-to-image/) - Generate images from text with the same 9B model
- [Flux 2 | Klein | 4B | Base | Edit](../flux-2-klein-4b-base-edit/) - Lighter 4B variant for faster editing
- [Flux 2 | Turbo | Edit](../flux-2-turbo-edit/) - Turbo variant for faster edits
- [Flux 2 | Flash | Edit](../flux-2-flash-edit/) - Flash variant for quick edits

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
