---
name: sdxl-ad-inpaint
description: "SDXL Ad Inpaint | Product Ad Image Generation. Generate product advertisement images with inpainting using SDXL. Triggers: sdxl ad inpaint, product ad, ad generation, product photography, ad inpainting"
allowed-tools: Bash(curl *), WebFetch
---

# SDXL Ad Inpaint

Generate product advertisement images with inpainting using SDXL. Place products in professional ad settings with configurable composition, refinement steps, and product fill options.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-ad-inpaint",
    "version": "0.0.1",
    "input": {
      "prompt": "a premium skincare product on a marble surface with rose petals, luxury beauty advertisement, studio lighting",
      "image": "https://example.com/product-cutout.jpg",
      "guidance_scale": 7.5,
      "num_inference_steps": 40,
      "img_size": "1024, 1024"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| apply_img | boolean | true | Apply image as input to guide the model |
| condition_scale | number | 0.9 | Condition scale for ControlNet strength |
| guidance_scale | number | 7.5 | Guidance scale for generation |
| image | string | - | Input image to guide the output |
| img_size | string | 1024, 1024 | Image size dimensions |
| negative_prompt | string | low quality, out of frame, illustration, 3d, sepia, painting, cartoons, sketch, watermark, text, Logo, advertisement | Negative prompt |
| num_inference_steps | integer | 40 | Number of inference steps |
| num_refine_steps | integer | 10 | Additional refinement passes |
| product_fill | string | Original | Product fill mode. enum: Original, 80, 70, 60, 50, 40, 30, 20 |
| prompt | string | - | Text prompt for ad generation |
| scheduler | string | K_EULER | Scheduler. enum: DDIM, DPMSolverMultistep, HeunDiscrete, KarrasDPM, K_EULER_ANCESTRAL, K_EULER, PNDM |
| seed | integer | - | Random seed for reproducibility |

## Examples

**Luxury product ad:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-ad-inpaint",
    "version": "0.0.1",
    "input": {
      "prompt": "a premium perfume bottle on a reflective gold surface, dramatic studio lighting, luxury advertisement, bokeh background",
      "image": "https://example.com/perfume-bottle.jpg",
      "guidance_scale": 8,
      "num_inference_steps": 50,
      "num_refine_steps": 15,
      "product_fill": "70",
      "scheduler": "KarrasDPM"
    }
  }'
```

**Food product photography:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sdxl-ad-inpaint",
    "version": "0.0.1",
    "input": {
      "prompt": "a fresh juice bottle on a rustic wooden table with fresh fruits and herbs, natural daylight, food photography",
      "image": "https://example.com/juice-bottle.jpg",
      "guidance_scale": 7.5,
      "num_inference_steps": 40,
      "condition_scale": 0.85,
      "seed": 42
    }
  }'
```

## Related Models

- [realistic-background](../realistic-background/) - Background replacement
- [flux-fill-pro](../flux-fill-pro/) - Flux-based inpainting
- [stable-diffusion-inpainting](../stable-diffusion-inpainting/) - Standard SD inpainting

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
