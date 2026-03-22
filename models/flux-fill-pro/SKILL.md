---
name: flux-fill-pro
description: "Flux Fill Pro | AI Inpainting. Fill and replace parts of images using masks with text-guided generation. Triggers: flux fill, inpainting, image fill, mask fill, flux inpaint"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Fill Pro

Inpaint and fill parts of images using masks with text-guided generation. Flux Fill Pro uses a black-and-white mask to identify areas to regenerate, guided by a text prompt.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-fill-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a beautiful flower garden with roses and tulips",
      "image": "https://example.com/garden-photo.jpg",
      "mask": "https://example.com/garden-mask.jpg",
      "guidance": 3,
      "steps": 50
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| guidance | number | 3 | Controls the balance between adherence to text prompt and image quality |
| image | string | - | The image to inpaint. Can contain an alpha mask |
| mask | string | - | A black-and-white image describing the part to inpaint. Black areas are preserved |
| output_format | string | jpg | Output format. enum: jpg, png |
| prompt | string | - | Text prompt for image generation |
| prompt_upsampling | boolean | false | Automatically modify the prompt for more creative generation |
| safety_tolerance | integer | 2 | Safety tolerance, 1 is most strict and 6 is most permissive |
| seed | integer | - | Random seed. Set for reproducible generation |
| steps | integer | 50 | Number of diffusion steps. Higher values yield finer details |

## Examples

**Object replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-fill-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a sleek modern sports car, metallic red, studio lighting",
      "image": "https://example.com/parking-lot.jpg",
      "mask": "https://example.com/car-area-mask.jpg",
      "guidance": 4,
      "steps": 50,
      "output_format": "png"
    }
  }'
```

**Background replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-fill-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a tropical beach with palm trees and turquoise water, sunny day",
      "image": "https://example.com/person-photo.jpg",
      "mask": "https://example.com/background-mask.jpg",
      "guidance": 3,
      "steps": 40,
      "seed": 99
    }
  }'
```

## Related Models

- [stable-diffusion-inpainting](../stable-diffusion-inpainting/) - Classic SD inpainting
- [realisitic-vision-v3-inpainting](../realisitic-vision-v3-inpainting/) - Realistic inpainting
- [sdxl-ad-inpaint](../sdxl-ad-inpaint/) - SDXL-based ad inpainting

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
