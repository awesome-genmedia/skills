---
name: tencent-flux-srpo-image-to-image
description: "Tencent | Flux | Srpo | Image to Image. Transform and enhance images using Tencent Flux SRPO model. Triggers: tencent, flux, srpo, image to image, image enhance, image transform"
allowed-tools: Bash(curl *), WebFetch
---

# Tencent | Flux | Srpo | Image to Image

Transform and enhance images using the Tencent Flux SRPO model. Supports acceleration modes, configurable strength for balancing between the original image and the generated output, and adjustable guidance scale.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "tencent-flux-srpo-image-to-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/photo.jpg",
      "prompt": "Enhance this photo with vivid colors and sharp details",
      "strength": 0.95,
      "guidance_scale": 4.5,
      "output_format": "jpeg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| acceleration | string | none | Generation speed. enum: none, regular, high |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled |
| guidance_scale | number | 4.5 | CFG scale for prompt adherence |
| image_url | string | | The URL of the image to transform |
| num_images | integer | | The number of images to generate |
| num_inference_steps | integer | 40 | The number of inference steps to perform |
| output_format | string | jpeg | The format of the generated image. enum: jpeg, png |
| prompt | string | | The prompt for image transformation |
| seed | string | | Seed for reproducible results |
| strength | number | 0.95 | Strength of the transformation (higher values = stronger transformation) |

## Examples

**Style transformation with high strength:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "tencent-flux-srpo-image-to-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Transform into a vibrant digital painting with dramatic sky colors",
      "strength": 0.98,
      "guidance_scale": 5.0,
      "num_inference_steps": 50,
      "output_format": "png"
    }
  }'
```

**Subtle enhancement with acceleration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "tencent-flux-srpo-image-to-image",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "prompt": "Enhance lighting and add soft bokeh to the background",
      "strength": 0.7,
      "acceleration": "regular",
      "guidance_scale": 4.5,
      "seed": "42"
    }
  }'
```

## Related Models

- [tencent-flux-srpo-text-to-image](../tencent-flux-srpo-text-to-image/) - Text to image with Tencent Flux SRPO
- [tencent-flux-1-srpo-text-to-image](../tencent-flux-1-srpo-text-to-image/) - Text to image with Tencent Flux 1 SRPO
- [topaz-upscale-image](../topaz-upscale-image/) - Image upscaling

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
