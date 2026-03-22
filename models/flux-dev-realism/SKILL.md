---
name: flux-dev-realism
description: "Flux Realism | Photorealistic AI Image Generation. Generate photorealistic images with Flux Dev enhanced by a realism LoRA. Triggers: flux realism, realistic image, photorealistic, flux realistic, photo generation"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Realism

Generate photorealistic images using Flux Dev enhanced with a realism LoRA. Optimized for lifelike photographs with configurable LoRA strength and guidance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev-realism",
    "version": "0.0.1",
    "input": {
      "prompt": "A photo of a woman, headshot, realistic, natural lighting",
      "aspect_ratio": "4:5",
      "lora_strength": 0.8,
      "num_inference_steps": 30,
      "guidance": 3.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 1:1, 16:9, 21:9, 2:3, 3:2, 4:5, 5:4, 9:16, 9:21 |
| guidance | number | 3.5 | Guidance controls adherence to the text prompt |
| lora_strength | number | 0.8 | LoRA strength controls the intensity of the realism effect |
| num_inference_steps | integer | 30 | Number of inference steps |
| num_outputs | integer | 1 | Number of outputs to generate |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 80 | Quality of output images, from 0 to 100 |
| prompt | string | A photo of a woman, headshot, realistic | Text prompt for generation |
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Professional headshot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev-realism",
    "version": "0.0.1",
    "input": {
      "prompt": "Professional corporate headshot of a man in a navy suit, clean white background, studio lighting, sharp focus",
      "aspect_ratio": "4:5",
      "lora_strength": 0.9,
      "num_inference_steps": 35,
      "guidance": 4,
      "output_format": "jpg",
      "output_quality": 95
    }
  }'
```

**Realistic street photography:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev-realism",
    "version": "0.0.1",
    "input": {
      "prompt": "A candid street photograph of a busy market in Marrakech, vibrant colors, natural sunlight, shot on 35mm film",
      "aspect_ratio": "3:2",
      "lora_strength": 0.8,
      "num_inference_steps": 30,
      "num_outputs": 2,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-dev](../flux-dev/) - Standard Flux Dev generation
- [flux-1-1-pro](../flux-1-1-pro/) - Professional Flux generation
- [realistic-vision-v6-0-b1](../realistic-vision-v6-0-b1/) - Realistic Vision image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
