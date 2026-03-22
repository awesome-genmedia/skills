---
name: illusion-diffusion-hq
description: "Illusion Diffusion | QR Code Art Generator. Generate artistic QR codes and optical illusion images from prompts. Triggers: illusion diffusion, qr code art, qr code, optical illusion, artistic qr"
allowed-tools: Bash(curl *), WebFetch
---

# Illusion Diffusion

Generate artistic QR codes and optical illusion images from text prompts. Create beautiful, functional QR codes that blend art with utility, or generate optical illusion artwork from custom images.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "illusion-diffusion-hq",
    "version": "0.0.1",
    "input": {
      "prompt": "a beautiful enchanted forest with magical creatures and glowing plants",
      "qr_code_content": "https://eachlabs.ai",
      "guidance_scale": 7.5,
      "num_inference_steps": 40
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| border | integer | 1 | QR code border size |
| controlnet_conditioning_scale | number | 1 | ControlNet conditioning strength multiplier |
| guidance_scale | number | 7.5 | Scale for classifier-free guidance |
| height | integer | 768 | Height of the output image |
| image | string | - | Input image. If none is provided, a QR code will be generated |
| negative_prompt | string | ugly, disfigured, low quality, blurry, nsfw | Negative prompt to guide generation |
| num_inference_steps | integer | 40 | Number of diffusion steps |
| num_outputs | integer | 1 | Number of outputs |
| prompt | string | - | The prompt to guide QR Code generation |
| qr_code_content | string | - | The website/content your QR Code will point to |
| qrcode_background | string | gray | QR code background color. enum: gray, white |
| seed | integer | -1 | Seed for reproducibility |
| width | integer | 768 | Width of the output image |

## Examples

**Business card QR code art:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "illusion-diffusion-hq",
    "version": "0.0.1",
    "input": {
      "prompt": "an elegant Japanese ink painting with cherry blossoms and a mountain, minimalist",
      "qr_code_content": "https://myportfolio.com",
      "controlnet_conditioning_scale": 0.9,
      "guidance_scale": 8,
      "num_inference_steps": 50,
      "qrcode_background": "white"
    }
  }'
```

**Optical illusion from custom image:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "illusion-diffusion-hq",
    "version": "0.0.1",
    "input": {
      "prompt": "a surreal dreamscape with floating islands and cosmic nebulae, detailed fantasy art",
      "image": "https://example.com/spiral-pattern.jpg",
      "controlnet_conditioning_scale": 1.2,
      "guidance_scale": 7.5,
      "num_inference_steps": 45,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-dev](../flux-dev/) - Text-to-image generation
- [stable-diffusion-3-5-large](../stable-diffusion-3-5-large/) - SD 3.5 image generation
- [recraft-v3](../recraft-v3/) - Styled image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
