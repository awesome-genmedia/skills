---
name: realistic-background
description: "Editing Image Background | AI Background Replacement. Replace image backgrounds with realistic AI-generated scenes. Triggers: background replacement, change background, realistic background, background editing, background swap"
allowed-tools: Bash(curl *), WebFetch
---

# Editing Image Background

Replace image backgrounds with realistic AI-generated scenes. Automatically segments the foreground subject and generates a new background based on a text prompt.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-background",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/product-photo.jpg",
      "prompt": "RAW photo, 8k uhd, dslr, soft lighting, high quality, modern kitchen countertop with marble surface",
      "cfg_scale": 7,
      "steps": 20,
      "denoising_strength": 0.75
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| cfg_scale | integer | 7 | CFG scale for guidance strength |
| denoising_strength | number | 0.75 | Denoising strength |
| image | string | - | Image to replace background |
| max_height | integer | 1024 | Maximum output height |
| max_width | integer | 1024 | Maximum output width |
| negative_prompt | string | (deformed, distorted, disfigured:1.3), poorly drawn, bad anatomy... | Negative prompt |
| only_masked_padding_pixels | integer | 4 | Only masked padding pixels |
| prompt | string | RAW photo, 8k uhd, dslr, soft lighting, high quality, film grain, Fujifilm XT3 | Prompt for background generation |
| sampler_name | string | DPM++ SDE Karras | Sampler. enum: DPM++ 2M, DPM++ SDE, DPM++ 2M SDE, DPM++ 2M SDE Heun, DPM++ 2S a, DPM++ 3M SDE, Euler a, Euler, LMS, Heun, DPM2, DPM2 a, DPM fast, DPM adaptive, Restart |
| seed | integer | 1 | Seed |
| steps | integer | 20 | Steps |

## Examples

**Product on a studio surface:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-background",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/watch-photo.jpg",
      "prompt": "RAW photo, 8k uhd, luxury product photography, dark slate surface, dramatic studio lighting, soft reflections",
      "cfg_scale": 8,
      "steps": 25,
      "denoising_strength": 0.8,
      "sampler_name": "DPM++ SDE Karras"
    }
  }'
```

**Portrait with outdoor background:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realistic-background",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/portrait.jpg",
      "prompt": "RAW photo, 8k uhd, beautiful cherry blossom garden in spring, soft natural lighting, bokeh background",
      "cfg_scale": 7,
      "steps": 20,
      "denoising_strength": 0.7,
      "seed": 42
    }
  }'
```

## Related Models

- [rembg](../rembg/) - Background removal
- [flux-fill-pro](../flux-fill-pro/) - Inpainting and fill
- [sdxl-ad-inpaint](../sdxl-ad-inpaint/) - Product ad inpainting

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
