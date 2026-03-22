---
name: flux-depth-dev
description: "Flux Depth Dev | Depth-Controlled Image Generation. Generate images guided by automatically extracted depth maps. Triggers: flux depth dev, depth control, depth map, image generation, controlnet depth"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Depth Dev

Generate images using depth map control with the Flux Dev model. Automatically generates depth maps from control images to guide image generation with configurable output options.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-depth-dev",
    "version": "0.0.1",
    "input": {
      "prompt": "a cozy cabin in a snowy mountain landscape, warm lights glowing from windows",
      "control_image": "https://example.com/landscape.jpg",
      "guidance": 10,
      "num_inference_steps": 28
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| control_image | string | - | Image used to control the generation. The depth map will be automatically generated |
| disable_safety_checker | boolean | false | Disable safety checker for generated images |
| guidance | number | 10 | Guidance for generated image |
| megapixels | string | 1 | Resolution scale. enum: 1, 0.25 |
| num_inference_steps | integer | 28 | Number of denoising steps. Recommended range is 28-50 |
| num_outputs | integer | 1 | Number of outputs to generate |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 80 | Quality when saving output images, from 0 to 100 |
| prompt | string | - | Prompt for generated image |
| seed | integer | - | Random seed. Set for reproducible generation |

## Examples

**Interior design transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-depth-dev",
    "version": "0.0.1",
    "input": {
      "prompt": "a modern minimalist living room with Scandinavian furniture, natural light, white walls",
      "control_image": "https://example.com/room-photo.jpg",
      "guidance": 12,
      "num_inference_steps": 35,
      "output_format": "png",
      "output_quality": 95
    }
  }'
```

**Multiple outputs with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-depth-dev",
    "version": "0.0.1",
    "input": {
      "prompt": "a medieval castle on a hill, dramatic storm clouds, dark fantasy style",
      "control_image": "https://example.com/hill-scene.jpg",
      "num_outputs": 2,
      "num_inference_steps": 40,
      "guidance": 8,
      "seed": 777
    }
  }'
```

## Related Models

- [flux-depth-pro](../flux-depth-pro/) - Depth-controlled generation (pro version)
- [flux-canny-pro](../flux-canny-pro/) - Edge-controlled image generation
- [flux-dev-controlnet](../flux-dev-controlnet/) - Multi-mode ControlNet generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
