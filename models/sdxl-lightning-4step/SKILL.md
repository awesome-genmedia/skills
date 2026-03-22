---
name: sdxl-lightning-4step
description: "SDXL-Lightning by ByteDance | Ultra-Fast Image Generation. Generate images in just 4 steps with SDXL Lightning. Triggers: sdxl lightning, bytedance, fast sdxl, 4 step, quick image generation"
allowed-tools: Bash(curl *), WebFetch
---

# SDXL-Lightning by ByteDance

Generate images in just 4 steps with SDXL Lightning by ByteDance. Optimized for ultra-fast generation while maintaining quality, ideal for rapid prototyping and real-time applications.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-lightning-4step",
    "version": "0.0.1",
    "input": {
      "prompt": "A superhero smiling, bright colors, dynamic pose",
      "width": 1024,
      "height": 1024,
      "num_inference_steps": 4,
      "scheduler": "K_EULER"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| disable_safety_checker | boolean | true | Disable safety checker for generated images |
| guidance_scale | number | 0 | Controls how much to follow the prompt vs generating creatively |
| height | integer | 1024 | Height of generated image |
| negative_prompt | string | worst quality, low quality | Exclude from generated content |
| num_inference_steps | integer | 4 | Number of processing steps |
| num_outputs | integer | 1 | Number of outputs to generate |
| prompt | string | A superhero smiling | Text prompt for generation |
| scheduler | string | K_EULER | Scheduler. enum: DDIM, DPMSolverMultistep, HeunDiscrete, KarrasDPM, K_EULER_ANCESTRAL, K_EULER, PNDM, DPM++2MSDE |
| seed | integer | - | Random seed for reproducibility |
| width | integer | 1024 | Width of generated image |

## Examples

**Batch fast generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-lightning-4step",
    "version": "0.0.1",
    "input": {
      "prompt": "a cute robot character, 3D render, Pixar style, colorful, detailed",
      "negative_prompt": "blurry, low quality, distorted, ugly",
      "width": 1024,
      "height": 1024,
      "num_outputs": 4,
      "num_inference_steps": 4,
      "seed": 42
    }
  }'
```

**Portrait with custom scheduler:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-lightning-4step",
    "version": "0.0.1",
    "input": {
      "prompt": "a beautiful woman with flowing red hair, dramatic lighting, professional photography",
      "width": 768,
      "height": 1024,
      "num_inference_steps": 4,
      "scheduler": "DPMSolverMultistep"
    }
  }'
```

## Related Models

- [flux-schnell](../flux-schnell/) - Fast Flux generation in 4 steps
- [flux-dev](../flux-dev/) - Higher quality Flux generation
- [stable-diffusion-3-5-large](../stable-diffusion-3-5-large/) - SD 3.5 image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
