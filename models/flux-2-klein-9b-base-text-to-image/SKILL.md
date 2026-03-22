---
name: flux-2-klein-9b-base-text-to-image
description: "Flux 2 | Klein | 9B | Base | Text to Image. Generate images from text prompts using the Flux 2 Klein 9B model. Triggers: text to image, image generation, flux generate, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Klein | 9B | Base | Text to Image

Generate high-quality images from text descriptions using the Flux 2 Klein 9B Base model. Supports various image sizes, guidance scales, and output formats.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A serene Japanese garden with cherry blossoms, koi pond, and wooden bridge at sunset",
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
| image_size | string | landscape_4_3 | The size of the image to generate. Options: `square_hd`, `square`, `portrait_4_3`, `portrait_16_9`, `landscape_4_3`, `landscape_16_9` |
| negative_prompt | string | - | Negative prompt for classifier-free guidance. Describes what to avoid in the image. |
| num_images | integer | 1 | The number of images to generate. |
| num_inference_steps | integer | 28 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to generate an image from. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Simple text-to-image generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A futuristic city skyline at night with neon lights reflecting on wet streets"
    }
  }'
```

**Portrait with high guidance:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Professional headshot of a business executive, studio lighting, sharp focus",
      "negative_prompt": "blurry, cartoon, illustration",
      "image_size": "portrait_4_3",
      "guidance_scale": 8,
      "num_inference_steps": 35,
      "seed": 12345
    }
  }'
```

**Batch generation with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-9b-base-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Minimalist flat design logo of a mountain with a sunrise",
      "num_images": 3,
      "acceleration": "high",
      "image_size": "square_hd",
      "output_format": "webp"
    }
  }'
```

## Related Models

- [Flux 2 | Klein | 9B | Base | Edit](../flux-2-klein-9b-base-edit/) - Edit existing images with the same 9B model
- [Flux 2 | Klein | 4B | Base | Text to Image](../flux-2-klein-4b-base-text-to-image/) - Lighter 4B variant for faster generation
- [Flux 2 | Turbo | Text to Image](../flux-2-turbo-text-to-image/) - Turbo variant for faster generation
- [Flux 2 | Max | Text to Image](../flux-2-max-text-to-image/) - Max quality variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
