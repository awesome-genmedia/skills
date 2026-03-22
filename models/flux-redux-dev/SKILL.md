---
name: flux-redux-dev
description: "Flux Redux Dev | Image Variation Generation. Generate high-quality image variations from an input image. Triggers: flux redux dev, image variation, image remix, redux, image to image"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Redux Dev

Generate high-quality image variations from an input image using Flux Redux Dev. Uses an input image instead of a text prompt to condition the output, with more inference steps than the Schnell variant for better quality.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-redux-dev",
    "version": "0.0.1",
    "input": {
      "redux_image": "https://example.com/input-photo.jpg",
      "aspect_ratio": "1:1",
      "guidance": 3,
      "num_inference_steps": 28
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 1:1, 16:9, 21:9, 3:2, 2:3, 4:5, 5:4, 3:4, 4:3, 9:16, 9:21 |
| disable_safety_checker | boolean | false | Disable safety checker for generated images |
| guidance | number | 3 | Guidance for generated image |
| megapixels | string | 1 | Resolution scale. enum: 1, 0.25 |
| num_inference_steps | integer | 28 | Number of denoising steps. Recommended range is 28-50 |
| num_outputs | integer | 1 | Number of outputs to generate |
| output_format | string | webp | Output format. enum: webp, jpg, png |
| output_quality | integer | 80 | Quality when saving output images, from 0 to 100 |
| redux_image | string | - | Input image to condition output on. Replaces prompt for Redux models |
| seed | integer | - | Random seed. Set for reproducible generation |

## Examples

**High-quality portrait variation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-redux-dev",
    "version": "0.0.1",
    "input": {
      "redux_image": "https://example.com/portrait.jpg",
      "aspect_ratio": "4:5",
      "guidance": 4,
      "num_inference_steps": 40,
      "output_format": "png",
      "output_quality": 100
    }
  }'
```

**Multiple variations with reproducibility:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-redux-dev",
    "version": "0.0.1",
    "input": {
      "redux_image": "https://example.com/artwork.jpg",
      "aspect_ratio": "16:9",
      "num_outputs": 3,
      "num_inference_steps": 35,
      "guidance": 3,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-redux-schnell](../flux-redux-schnell/) - Faster Redux variations with fewer steps
- [flux-1-1-pro-ultra](../flux-1-1-pro-ultra/) - Ultra-quality generation with Redux support
- [flux-dev](../flux-dev/) - Text-to-image generation with Flux Dev

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
