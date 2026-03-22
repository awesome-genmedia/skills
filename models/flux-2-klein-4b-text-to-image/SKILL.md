---
name: flux-2-klein-4b-text-to-image
description: "Flux 2 | Klein | 4B | Text to Image. Generate images from text with the enhanced 4B model including guidance and acceleration. Triggers: text to image, image generation, flux generate, ai art"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 2 | Klein | 4B | Text to Image

Generate images from text prompts using the enhanced Flux 2 Klein 4B model with classifier-free guidance and acceleration support. Balances speed and quality with configurable parameters.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A steampunk airship flying over Victorian London at dusk",
      "image_size": "landscape_4_3",
      "guidance_scale": 5,
      "num_inference_steps": 4,
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
| num_inference_steps | integer | 4 | The number of inference steps to perform. |
| output_format | string | png | The format of the generated image. Options: `jpeg`, `png`, `webp` |
| prompt | string | - | The prompt to generate an image from. |
| seed | integer | - | The seed to use for the generation. If not provided, a random seed will be used. |

## Examples

**Fast generation with high acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "A cute robot serving coffee in a diner, retro style",
      "acceleration": "high"
    }
  }'
```

**Detailed generation with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-2-klein-4b-text-to-image",
    "version": "0.0.1",
    "input": {
      "prompt": "Oil painting of a stormy seascape with a lighthouse, dramatic clouds",
      "negative_prompt": "blurry, flat, cartoon, text, watermark",
      "guidance_scale": 7.5,
      "num_inference_steps": 8,
      "image_size": "landscape_16_9",
      "output_format": "jpeg",
      "seed": 2024
    }
  }'
```

## Related Models

- [Flux 2 | Klein | 4B | Edit](../flux-2-klein-4b-edit/) - Edit images with the same 4B model
- [Flux 2 | Klein | 4B | Base | Text to Image](../flux-2-klein-4b-base-text-to-image/) - Base variant without guidance
- [Flux 2 | Klein | 9B | Base | Text to Image](../flux-2-klein-9b-base-text-to-image/) - Higher quality 9B variant

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
