---
name: flux-dev-controlnet
description: "Flux Controlnet | Multi-Mode Controlled Image Generation. Generate images with canny, depth, or soft edge control using Flux Dev. Triggers: flux controlnet, controlnet, canny, depth, soft edge, controlled generation"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Controlnet

Generate images with multi-mode ControlNet support using Flux Dev. Supports canny edge detection, depth maps, and soft edge control types with optional LoRA models.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "a stunning watercolor painting of a mountain village at sunset",
      "control_image": "https://example.com/village-photo.jpg",
      "control_type": "depth",
      "control_strength": 0.5,
      "guidance_scale": 3.5,
      "steps": 28
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| control_image | string | - | Image to use with ControlNet |
| control_strength | number | 0.5 | Strength of ControlNet. Different controls work better at different strengths |
| control_type | string | depth | Control mode. enum: canny, soft_edge, depth |
| depth_preprocessor | string | DepthAnything | Depth preprocessor. enum: Midas, Zoe, DepthAnything, Zoe-DepthAnything |
| guidance_scale | number | 3.5 | Guidance scale |
| image_to_image_strength | number | 0 | Strength of image-to-image control. 0 means no control, 1 means full |
| lora_strength | number | 1 | Strength of LoRA model |
| lora_url | string | - | Optional LoRA model URL (HuggingFace .safetensors or Replicate link) |
| negative_prompt | string | - | Things you do not want to see in the image |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 80 | Quality of output images, from 0 to 100 |
| prompt | string | - | Text prompt for generation |
| return_preprocessed_image | boolean | false | Return the preprocessed control image |
| seed | integer | - | Set a seed for reproducibility |
| soft_edge_preprocessor | string | HED | Soft edge preprocessor. enum: HED, TEED, PiDiNet |
| steps | integer | 28 | Number of steps |

## Examples

**Canny edge control:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "a cyberpunk cityscape at night, neon lights, rain-slicked streets, ultra detailed",
      "control_image": "https://example.com/city-skyline.jpg",
      "control_type": "canny",
      "control_strength": 0.6,
      "guidance_scale": 4,
      "steps": 30,
      "output_format": "png"
    }
  }'
```

**Soft edge with LoRA:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-dev-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "anime style illustration of a girl in a flower garden, Studio Ghibli",
      "control_image": "https://example.com/person-in-garden.jpg",
      "control_type": "soft_edge",
      "soft_edge_preprocessor": "HED",
      "control_strength": 0.4,
      "lora_url": "https://huggingface.co/my-org/anime-style-lora.safetensors",
      "lora_strength": 0.8,
      "steps": 35,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-canny-pro](../flux-canny-pro/) - Pro canny edge control
- [flux-depth-pro](../flux-depth-pro/) - Pro depth control
- [sdxl-controlnet](../sdxl-controlnet/) - SDXL-based ControlNet

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
