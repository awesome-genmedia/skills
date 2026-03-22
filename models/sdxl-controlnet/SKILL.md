---
name: sdxl-controlnet
description: "SDXL Controlnet | Controlled Image Generation. Generate images guided by input images using ControlNet with SDXL. Triggers: sdxl controlnet, controlnet, controlled generation, image to image, sdxl control"
allowed-tools: Bash(curl *), WebFetch
---

# SDXL Controlnet

Generate images guided by input images using ControlNet with the SDXL model. Control the generation process with a reference image and text prompt for precise structural guidance.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "aerial view, a futuristic research complex in a bright foggy jungle, hard lighting",
      "image": "https://example.com/reference-layout.jpg",
      "condition_scale": 0.5,
      "num_inference_steps": 50
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| condition_scale | number | 0.5 | ControlNet conditioning scale for generalization |
| image | string | - | Input image for img2img or inpaint mode |
| negative_prompt | string | low quality, bad quality, sketches | Input negative prompt |
| num_inference_steps | integer | 50 | Number of denoising steps |
| prompt | string | aerial view, a futuristic research complex... | Input prompt |
| seed | integer | 0 | Random seed. Set to 0 to randomize |

## Examples

**Architectural visualization:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "a modern glass skyscraper reflecting sunset clouds, photorealistic, architectural photography",
      "image": "https://example.com/building-sketch.jpg",
      "condition_scale": 0.7,
      "num_inference_steps": 50,
      "negative_prompt": "low quality, blurry, distorted"
    }
  }'
```

**Artistic style transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-controlnet",
    "version": "0.0.1",
    "input": {
      "prompt": "a vibrant oil painting of a garden path with blooming roses, impressionist style",
      "image": "https://example.com/garden-path.jpg",
      "condition_scale": 0.4,
      "num_inference_steps": 40,
      "seed": 12345
    }
  }'
```

## Related Models

- [flux-dev-controlnet](../flux-dev-controlnet/) - Flux-based multi-mode ControlNet
- [flux-canny-pro](../flux-canny-pro/) - Canny edge ControlNet with Flux
- [flux-depth-pro](../flux-depth-pro/) - Depth-controlled generation with Flux

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
