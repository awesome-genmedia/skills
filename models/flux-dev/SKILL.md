---
name: flux-dev
description: "Flux Dev | AI Image Generation. Generate high-quality images from text prompts with Flux Dev. Triggers: flux dev, flux, text to image, image generation, ai image"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Dev

Generate high-quality images from text prompts using Flux Dev. Supports text-to-image and image-to-image modes with configurable aspect ratio, guidance, and quality settings.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev",
    "version": "0.0.1",
    "input": {
      "prompt": "a photorealistic portrait of a woman in a sunlit garden, shallow depth of field, golden hour",
      "aspect_ratio": "4:5",
      "guidance": 3.5,
      "num_inference_steps": 28,
      "output_format": "webp"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 1:1, 16:9, 21:9, 2:3, 3:2, 4:5, 5:4, 9:16, 9:21 |
| disable_safety_checker | boolean | false | Disable safety checker for generated images |
| guidance | number | 3.5 | Guidance for generated image |
| image | string | - | Input image for image-to-image mode |
| num_inference_steps | integer | 28 | Number of denoising steps. Recommended range is 28-50 |
| num_outputs | integer | 1 | Number of outputs to generate |
| output_format | string | webp | Output format. enum: webp, png, jpg |
| output_quality | integer | 80 | Quality when saving output images, from 0 to 100 |
| prompt | string | - | Prompt for generated image |
| prompt_strength | number | 0.8 | Prompt strength when using img2img. 1.0 is full destruction of input |
| seed | integer | - | Random seed. Set for reproducible generation |

## Examples

**Landscape with high detail:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev",
    "version": "0.0.1",
    "input": {
      "prompt": "a sweeping aerial view of Patagonian mountains and glaciers, dramatic clouds, National Geographic style, 8k",
      "aspect_ratio": "21:9",
      "guidance": 4,
      "num_inference_steps": 40,
      "output_format": "png",
      "output_quality": 100
    }
  }'
```

**Image-to-image transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev",
    "version": "0.0.1",
    "input": {
      "prompt": "a vibrant pop art illustration in the style of Andy Warhol",
      "image": "https://example.com/portrait.jpg",
      "prompt_strength": 0.75,
      "guidance": 3.5,
      "num_inference_steps": 30,
      "seed": 42
    }
  }'
```

**Multiple outputs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev",
    "version": "0.0.1",
    "input": {
      "prompt": "a cute robot assistant holding a coffee cup, 3D render, soft lighting, pastel colors",
      "aspect_ratio": "1:1",
      "num_outputs": 3,
      "guidance": 3.5,
      "num_inference_steps": 28
    }
  }'
```

## Related Models

- [flux-schnell](../flux-schnell/) - Fast Flux generation with fewer steps
- [flux-1-1-pro](../flux-1-1-pro/) - Professional quality Flux generation
- [flux-1-1-pro-ultra](../flux-1-1-pro-ultra/) - Ultra quality Flux generation
- [flux-dev-realism](../flux-dev-realism/) - Flux with realism LoRA

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
