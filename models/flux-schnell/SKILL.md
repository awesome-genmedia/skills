---
name: flux-schnell
description: "Flux Schnell | Fast AI Image Generation. Generate images quickly from text prompts with Flux Schnell in just 4 steps. Triggers: flux schnell, fast image, quick generation, text to image, flux fast"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Schnell

Generate images quickly from text prompts with Flux Schnell. Optimized for speed with just 4 denoising steps, making it ideal for rapid prototyping and real-time applications.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-schnell",
    "version": "0.0.1",
    "input": {
      "prompt": "a cozy reading nook with floor-to-ceiling bookshelves, warm afternoon light streaming through a window",
      "aspect_ratio": "1:1",
      "num_inference_steps": 4,
      "output_format": "webp"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21 |
| disable_safety_checker | boolean | true | Disable safety checker for generated images |
| go_fast | boolean | true | Run faster with fp8 quantized model optimized for speed |
| megapixels | string | 1 | Resolution scale. enum: 1, 0.25 |
| num_inference_steps | integer | 4 | Number of denoising steps |
| num_outputs | integer | 1 | Number of images to generate |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 80 | Quality when saving output images, from 0 to 100 |
| prompt | string | - | Prompt for generated image |
| seed | integer | - | Random seed. Set for reproducible generation |

## Examples

**Quick batch generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-schnell",
    "version": "0.0.1",
    "input": {
      "prompt": "a minimalist logo design for a tech startup, clean lines, modern typography",
      "aspect_ratio": "1:1",
      "num_outputs": 4,
      "num_inference_steps": 4,
      "output_format": "png"
    }
  }'
```

**Widescreen cinematic:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-schnell",
    "version": "0.0.1",
    "input": {
      "prompt": "an epic battle scene between samurai warriors on a misty bridge, cinematic composition, dramatic lighting",
      "aspect_ratio": "21:9",
      "num_inference_steps": 4,
      "go_fast": true,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-dev](../flux-dev/) - Higher quality Flux with more steps
- [flux-1-1-pro](../flux-1-1-pro/) - Professional quality Flux
- [flux-dev-realism](../flux-dev-realism/) - Photorealistic Flux generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
