---
name: flux-canny-pro
description: "Flux Canny Pro | Edge-Controlled Image Generation. Generate images guided by edge detection from control images. Triggers: flux canny, canny edge, edge control, image generation, controlnet canny"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Canny Pro

Generate images guided by canny edge detection from control images. Flux Canny Pro extracts edges from an input image to preserve structural composition while generating new content.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-canny-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a futuristic city at night, neon lights, cyberpunk aesthetic",
      "control_image": "https://example.com/city-photo.jpg",
      "guidance": 30,
      "steps": 50,
      "output_format": "jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| control_image | string | - | Image to use as control input. Must be jpeg, png, or webp |
| guidance | number | 30 | Controls the balance between adherence to text/image prompt and creativity |
| output_format | string | jpg | Output format. enum: jpg, png |
| prompt | string | - | Text prompt for image generation |
| prompt_upsampling | boolean | false | Automatically modify the prompt for more creative generation |
| safety_tolerance | integer | 2 | Safety tolerance, 1 is most strict and 6 is most permissive |
| seed | integer | - | Random seed. Set for reproducible generation |
| steps | integer | 50 | Number of diffusion steps. Higher values yield finer details |

## Examples

**Architectural style transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-canny-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a gothic cathedral made of crystal and ice, fantasy art, detailed",
      "control_image": "https://example.com/cathedral.jpg",
      "guidance": 25,
      "steps": 50,
      "seed": 123
    }
  }'
```

**Product design reimagining:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-canny-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a sleek minimalist white ceramic vase, studio lighting, product photography",
      "control_image": "https://example.com/vase-shape.jpg",
      "guidance": 20,
      "steps": 40,
      "prompt_upsampling": true,
      "output_format": "png"
    }
  }'
```

## Related Models

- [flux-depth-pro](../flux-depth-pro/) - Depth-controlled image generation
- [flux-dev-controlnet](../flux-dev-controlnet/) - Multi-mode ControlNet generation
- [sdxl-controlnet](../sdxl-controlnet/) - SDXL-based ControlNet generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
