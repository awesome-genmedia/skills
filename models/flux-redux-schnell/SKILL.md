---
name: flux-redux-schnell
description: "Flux Redux Schnell | Image Variation Generation. Generate image variations from an input image at high speed. Triggers: flux redux, flux schnell, image variation, image remix, fast image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Redux Schnell

Generate fast image variations from an input image using Flux Redux Schnell. This model uses an input image instead of a text prompt to condition the output, creating variations of the source image.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-redux-schnell",
    "version": "0.0.1",
    "input": {
      "redux_image": "https://example.com/input-photo.jpg",
      "aspect_ratio": "1:1",
      "num_inference_steps": 4,
      "output_format": "webp"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21 |
| disable_safety_checker | boolean | false | Disable safety checker for generated images |
| megapixels | string | 1 | Resolution scale. enum: 1, 0.25 |
| num_inference_steps | integer | 4 | Number of denoising steps. 4 is recommended |
| num_outputs | integer | 1 | Number of outputs to generate |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 80 | Quality when saving output images, from 0 to 100 |
| redux_image | string | - | Input image to condition output on. Replaces prompt for Redux models |
| seed | integer | - | Random seed. Set for reproducible generation |

## Examples

**Portrait variation in 16:9:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-redux-schnell",
    "version": "0.0.1",
    "input": {
      "redux_image": "https://example.com/portrait.jpg",
      "aspect_ratio": "16:9",
      "num_outputs": 2,
      "output_format": "png",
      "output_quality": 95
    }
  }'
```

**Quick variation with fixed seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-redux-schnell",
    "version": "0.0.1",
    "input": {
      "redux_image": "https://example.com/landscape.jpg",
      "aspect_ratio": "3:2",
      "num_inference_steps": 4,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-redux-dev](../flux-redux-dev/) - Higher quality Redux variations with more steps
- [flux-schnell](../flux-schnell/) - Fast text-to-image generation
- [flux-1-1-pro-ultra](../flux-1-1-pro-ultra/) - Ultra-quality image generation with Redux support

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
