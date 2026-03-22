---
name: sana
description: "Sana by Nvidia | AI Image Generation. Generate images from text prompts with PAG guidance support. Triggers: sana, nvidia sana, text to image, image generation, ai image"
allowed-tools: Bash(curl *), WebFetch
---

# Sana by Nvidia

Generate high-quality images from text prompts using Nvidia's Sana model. Supports classifier-free guidance, PAG guidance, and configurable resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sana",
    "version": "0.0.1",
    "input": {
      "prompt": "a cyberpunk cat with a neon sign that says Sana",
      "width": 1024,
      "height": 1024,
      "num_inference_steps": 18,
      "guidance_scale": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| guidance_scale | number | 5 | Classifier-free guidance scale |
| height | integer | 1024 | Height of output image |
| negative_prompt | string | - | Specify things to not see in the output |
| num_inference_steps | integer | 18 | Number of denoising steps |
| pag_guidance_scale | number | 2 | PAG Guidance scale |
| prompt | string | a cyberpunk cat with a neon sign... | Input prompt |
| seed | integer | - | Random seed. Leave blank to randomize |
| width | integer | 1024 | Width of output image |

## Examples

**Detailed landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sana",
    "version": "0.0.1",
    "input": {
      "prompt": "a serene Japanese garden with a koi pond, cherry blossoms falling, golden hour lighting, photorealistic",
      "width": 1024,
      "height": 768,
      "guidance_scale": 6,
      "pag_guidance_scale": 2.5,
      "num_inference_steps": 25
    }
  }'
```

**Character illustration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sana",
    "version": "0.0.1",
    "input": {
      "prompt": "a futuristic astronaut exploring an alien marketplace, vibrant colors, concept art style",
      "width": 1024,
      "height": 1024,
      "negative_prompt": "blurry, low quality, distorted",
      "guidance_scale": 5,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-schnell](../flux-schnell/) - Fast image generation with Flux
- [stable-diffusion-3-5-large](../stable-diffusion-3-5-large/) - Stable Diffusion 3.5 image generation
- [recraft-v3](../recraft-v3/) - Image generation with style control

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
