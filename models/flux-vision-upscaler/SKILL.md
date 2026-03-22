---
name: flux-vision-upscaler
description: "Flux Vision Upscaler. Upscale images with creative control up to 4x. Triggers: image upscaling, flux, enhance, super resolution, upscale"
allowed-tools: Bash(curl *), WebFetch
---

# Flux Vision Upscaler

Upscale images up to 4x with configurable creativity and guidance controls. Balance between faithful upscaling and creative enhancement.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-vision-upscaler",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/low-res-image.jpg",
      "upscale_factor": 2,
      "creativity": 0.3
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| creativity | number | 0.3 | The creativity level. Higher values add more model-generated detail. |
| enable_safety_checker | boolean | true | Whether to enable the safety checker. |
| guidance | number | 1 | CFG/guidance scale (0-20). Controls how closely the model follows guidance. |
| image_url | string | | The URL of the image to upscale. |
| seed | string | | The seed for reproducible results. |
| steps | integer | 20 | Number of inference steps (4-50). |
| upscale_factor | number | 2 | The upscale factor (1-4x). |

## Examples

**High-fidelity 4x upscale:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-vision-upscaler",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/thumbnail.jpg",
      "upscale_factor": 4,
      "creativity": 0.2,
      "steps": 30,
      "guidance": 2
    }
  }'
```

**Creative enhancement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-vision-upscaler",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/old-photo.jpg",
      "upscale_factor": 2,
      "creativity": 0.6,
      "steps": 25,
      "seed": "42"
    }
  }'
```

## Related Models

- [Topaz Upscale Video](../topaz-upscale-video/) - Video upscaling
- [Topaz Upscale Image](../topaz-upscale-image/) - Alternative image upscaler

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
