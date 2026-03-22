---
name: each-upscaler
description: "Image Upscaler by Each AI | AI Image Upscaling. Upscale images with creativity and resemblance controls, face enhancement, and multiple SD models. Triggers: upscaler, upscale, image upscale, each upscaler, enhance image, super resolution"
allowed-tools: Bash(curl *), WebFetch
---

# Image Upscaler by Each AI

Upscale images with advanced controls for creativity, resemblance, sharpening, and optional face/hand enhancement. Supports multiple Stable Diffusion base models and schedulers.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "each-upscaler",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/low-res-photo.jpg",
      "scale_factor": 2,
      "creativity": 0.35,
      "resemblance": 0.6,
      "num_inference_steps": 18
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| creativity | number | 0.35 | Creativity level, try from 0.3 - 0.9 |
| custom_sd_model | string | - | Custom SD model URL |
| downscaling | boolean | false | Downscale before upscaling. Can improve quality for large images |
| downscaling_resolution | integer | 768 | Downscaling resolution |
| dynamic | number | 6 | HDR effect, try from 3 - 9 |
| handfix | string | disabled | Hand fixing mode. enum: disabled, hands_only, image_and_hands |
| image | string | - | Input image |
| lora_links | string | - | Link to LoRA file(s) for upscaling |
| mask | string | - | Mask image to mark areas to preserve during upscaling |
| negative_prompt | string | (worst quality, low quality, normal quality:2)... | Negative prompt |
| num_inference_steps | integer | 18 | Number of denoising steps |
| output_format | string | png | Output format. enum: webp, jpg, png |
| pattern | boolean | false | Upscale a pattern with seamless tiling |
| prompt | string | masterpiece, best quality, highres... | Prompt |
| resemblance | number | 0.6 | Resemblance to original, try from 0.3 - 1.6 |
| scale_factor | number | 2 | Scale factor |
| scheduler | string | DPM++ 3M SDE Karras | Scheduler. enum: DPM++ 2M Karras, DPM++ SDE Karras, DPM++ 2M SDE Exponential, DPM++ 2M SDE Karras, Euler a, Euler, LMS, Heun, DPM2, DPM2 a, DPM++ 2S a, DPM++ 2M, DPM++ SDE, DPM++ 2M SDE, DPM++ 2M SDE Heun, and more |
| sd_model | string | juggernaut_reborn.safetensors | Base model. enum: epicrealism_naturalSinRC1VAE.safetensors, juggernaut_reborn.safetensors, flat2DAnimerge_v45Sharp.safetensors |
| seed | integer | 1337 | Random seed |
| sharpen | number | 0 | Sharpening intensity after upscaling |
| tiling_height | integer | 144 | Tiling height |
| tiling_width | integer | 112 | Tiling width |

## Examples

**High-quality portrait upscale with face fix:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "each-upscaler",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/portrait.jpg",
      "scale_factor": 2,
      "creativity": 0.4,
      "resemblance": 0.8,
      "handfix": "image_and_hands",
      "dynamic": 5,
      "output_format": "png"
    }
  }'
```

**Creative upscale with HDR:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "each-upscaler",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/landscape.jpg",
      "scale_factor": 4,
      "creativity": 0.6,
      "resemblance": 0.5,
      "dynamic": 8,
      "sharpen": 1.5,
      "sd_model": "epicrealism_naturalSinRC1VAE.safetensors [84d76a0328]",
      "num_inference_steps": 25
    }
  }'
```

## Related Models

- [real-esrgan](../real-esrgan/) - Real-ESRGAN face enhancer and upscaler
- [real-esrgan-a100](../real-esrgan-a100/) - Fast face enhancement
- [gfpgan](../gfpgan/) - GFPGAN face restoration

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
