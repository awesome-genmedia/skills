---
name: flux-depth-pro
description: "Flux Depth Pro | Depth-Controlled Image Generation. Generate images guided by depth maps from control images. Triggers: flux depth, depth control, depth map, image generation, flux pro depth"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Depth Pro

Generate images using depth map control from input images. Flux Depth Pro automatically extracts depth information from a control image to guide the generation process.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-depth-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a mystical forest scene with glowing mushrooms, fantasy art",
      "control_image": "https://example.com/reference-scene.jpg",
      "guidance": 10,
      "steps": 50,
      "output_format": "jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| control_image | string | - | Image to use as control input. Must be jpeg, png, gif, or webp |
| guidance | number | 10 | Controls the balance between adherence to text/image prompt and creativity |
| output_format | string | jpg | Output format. enum: jpg, png |
| prompt | string | - | Text prompt for image generation |
| prompt_upsampling | boolean | false | Automatically modify the prompt for more creative generation |
| safety_tolerance | integer | 2 | Safety tolerance, 1 is most strict and 6 is most permissive |
| seed | integer | - | Random seed. Set for reproducible generation |
| steps | integer | 50 | Number of diffusion steps. Higher values yield finer details |

## Examples

**Architecture reimagined:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-depth-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a futuristic cyberpunk building at night, neon lights, rain-slicked streets",
      "control_image": "https://example.com/building-photo.jpg",
      "guidance": 12,
      "steps": 50,
      "seed": 99
    }
  }'
```

**Stylized portrait with depth preservation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-depth-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "oil painting portrait of a Renaissance nobleman, dramatic lighting, museum quality",
      "control_image": "https://example.com/portrait-photo.jpg",
      "guidance": 8,
      "steps": 40,
      "prompt_upsampling": true,
      "output_format": "png"
    }
  }'
```

## Related Models

- [flux-depth-dev](../flux-depth-dev/) - Depth-controlled generation (dev version)
- [flux-canny-pro](../flux-canny-pro/) - Edge-controlled image generation
- [flux-dev-controlnet](../flux-dev-controlnet/) - Multi-mode ControlNet generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
