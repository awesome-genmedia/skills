---
name: realistic-vision-v6-0-b1
description: "Realistic Vision | Photorealistic Image Generation. Generate photorealistic images with img2img and inpainting support. Triggers: realistic vision, photorealistic, realistic image, photo generation, realistic portrait"
allowed-tools: Bash(curl *), WebFetch
---

# Realistic Vision

Generate photorealistic images from text prompts with Realistic Vision V6. Supports text-to-image, image-to-image, and inpainting with multiple scheduler options.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-vision-v6-0-b1",
    "version": "0.0.1",
    "input": {
      "prompt": "photo of offroad car, forest, sunset, clouds",
      "width": 512,
      "height": 728,
      "guidance_scale": 7.5,
      "num_inference_steps": 20
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| guidance_scale | number | 7.5 | Guidance scale - how much the model follows the prompt |
| height | integer | 728 | Height of generated image |
| image | string | - | Input image for img2img mode |
| mask | string | - | Mask for inpainting (specifies which parts to alter) |
| negative_prompt | string | (deformed iris, deformed pupils, semi-realistic, cgi, 3d, render, sketch, cartoon, drawing, anime)... | Negative prompt |
| num_inference_steps | integer | 20 | Number of inference steps |
| prompt | string | photo of offroad car, forest, sunset, clouds | Text prompt for generation |
| scheduler | string | K_EULER_ANCESTRAL | Scheduler. enum: DDIM, DPMSolverMultistep, HeunDiscrete, K_EULER_ANCESTRAL, K_EULER, PNDM |
| seed | integer | - | Random seed for reproducibility |
| strength | number | 1 | Strength of transformation when using img2img |
| use_karras_sigmas | boolean | false | Use Karras sigmas for improved image quality |
| width | integer | 512 | Width of generated image |

## Examples

**Photorealistic portrait:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-vision-v6-0-b1",
    "version": "0.0.1",
    "input": {
      "prompt": "RAW photo, a beautiful woman standing in golden wheat field, natural skin, 8k uhd, DSLR, film grain, Fujifilm XT3",
      "negative_prompt": "(deformed, distorted, disfigured:1.3), poorly drawn, bad anatomy, low quality, blurry",
      "width": 512,
      "height": 768,
      "guidance_scale": 7,
      "num_inference_steps": 25,
      "scheduler": "DPMSolverMultistep",
      "use_karras_sigmas": true
    }
  }'
```

**Image-to-image style transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-vision-v6-0-b1",
    "version": "0.0.1",
    "input": {
      "prompt": "RAW photo, a cozy cabin in snowy mountains, warm lights, 8k uhd, high quality",
      "image": "https://example.com/cabin-sketch.jpg",
      "strength": 0.75,
      "guidance_scale": 8,
      "num_inference_steps": 25,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-dev-realism](../flux-dev-realism/) - Flux-based photorealistic generation
- [realisitic-vision-v3-inpainting](../realisitic-vision-v3-inpainting/) - Realistic inpainting
- [flux-dev](../flux-dev/) - Flux Dev image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
