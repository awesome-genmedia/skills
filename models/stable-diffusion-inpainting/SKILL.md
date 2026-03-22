---
name: stable-diffusion-inpainting
description: "Stable Diffusion Inpainting | AI Image Inpainting. Edit and fill parts of images using masks and text prompts. Triggers: sd inpainting, inpaint, image editing, mask fill, stable diffusion inpaint"
allowed-tools: Bash(curl *), WebFetch
---

# Stable Diffusion Inpainting

Edit and fill parts of images using masks and text prompts with Stable Diffusion. Specify areas to regenerate with a black-and-white mask and guide the generation with a text prompt.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-inpainting",
    "version": "0.0.1",
    "input": {
      "prompt": "a beautiful garden with colorful flowers and butterflies",
      "image": "https://example.com/backyard.jpg",
      "mask": "https://example.com/mask.jpg",
      "guidance_scale": 7.5,
      "num_inference_steps": 50
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| disable_safety_checker | boolean | false | Disable safety checker for generated images |
| guidance_scale | number | 7.5 | Scale for classifier-free guidance |
| height | integer | 512 | Output image height |
| image | string | - | Initial image to generate variations of. Will be resized to height x width |
| mask | string | - | Black and white mask image. White areas are inpainted |
| negative_prompt | string | - | Specify things to not see in the output |
| num_inference_steps | integer | 50 | Number of denoising steps |
| num_outputs | integer | 1 | Number of images to generate |
| prompt | string | a vision of paradise. unreal engine | Input prompt |
| scheduler | string | DPMSolverMultistep | Scheduler. enum: DDIM, K_EULER, DPMSolverMultistep, K_EULER_ANCESTRAL, PNDM, KLMS |
| seed | integer | - | Random seed. Leave blank to randomize |
| width | integer | 512 | Output image width |

## Examples

**Object removal and replacement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-inpainting",
    "version": "0.0.1",
    "input": {
      "prompt": "a clean wooden desk with a laptop and a cup of coffee, office background",
      "image": "https://example.com/messy-desk.jpg",
      "mask": "https://example.com/desk-mask.jpg",
      "negative_prompt": "blurry, low quality, distorted",
      "guidance_scale": 8,
      "num_inference_steps": 50,
      "scheduler": "K_EULER"
    }
  }'
```

**Multiple inpainting outputs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "stable-diffusion-inpainting",
    "version": "0.0.1",
    "input": {
      "prompt": "a cute orange tabby cat sitting on a windowsill",
      "image": "https://example.com/window.jpg",
      "mask": "https://example.com/windowsill-mask.jpg",
      "num_outputs": 3,
      "guidance_scale": 7.5,
      "num_inference_steps": 40,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-fill-pro](../flux-fill-pro/) - Flux-based pro inpainting
- [realisitic-vision-v3-inpainting](../realisitic-vision-v3-inpainting/) - Realistic vision inpainting
- [sdxl-ad-inpaint](../sdxl-ad-inpaint/) - SDXL ad product inpainting

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
