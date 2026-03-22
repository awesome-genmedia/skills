---
name: realisitic-vision-v3-inpainting
description: "Realistic Vision V3 Inpainting | Photorealistic Inpainting. Fill and replace parts of images with photorealistic results. Triggers: realistic vision inpainting, realistic inpaint, photo inpainting, face inpainting, realistic editing"
allowed-tools: Bash(curl *), WebFetch
---

# Realistic Vision V3 Inpainting

Inpaint and fill parts of images with photorealistic results using Realistic Vision V3. Ideal for portrait editing, object replacement, and realistic image modifications.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realisitic-vision-v3-inpainting",
    "version": "0.0.1",
    "input": {
      "prompt": "RAW photo, a portrait photo of a woman smiling in a park, natural skin, 8k uhd, high quality, film grain, Fujifilm XT3",
      "image": "https://example.com/portrait.jpg",
      "mask": "https://example.com/mask.jpg",
      "steps": 20,
      "strength": 0.8
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| guaidance_scale | number | 7.5 | Higher guidance scale encourages images closely linked to text prompt |
| image | string | - | Input image |
| mask | string | - | Mask image |
| negative_prompt | string | (deformed iris, deformed pupils, semi-realistic, cgi, 3d, render, sketch, cartoon, drawing, anime:1.4)... | Negative prompt |
| num_outputs | integer | 1 | Number of images to create |
| prompt | string | RAW photo, a portrait photo... | Text prompt |
| steps | integer | 20 | Number of inference steps |
| strength | number | 0.8 | Strength/weight of the inpainting |

## Examples

**Face retouching:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realisitic-vision-v3-inpainting",
    "version": "0.0.1",
    "input": {
      "prompt": "RAW photo, a close-up portrait, flawless skin, natural lighting, 8k uhd, Fujifilm XT3",
      "image": "https://example.com/face-photo.jpg",
      "mask": "https://example.com/face-mask.jpg",
      "guaidance_scale": 8,
      "steps": 25,
      "strength": 0.7
    }
  }'
```

**Background replacement with multiple outputs:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "realisitic-vision-v3-inpainting",
    "version": "0.0.1",
    "input": {
      "prompt": "RAW photo, a beautiful beach with turquoise water, palm trees, golden sand, 8k uhd, high quality",
      "image": "https://example.com/person-outdoors.jpg",
      "mask": "https://example.com/background-mask.jpg",
      "num_outputs": 3,
      "steps": 25,
      "strength": 0.85
    }
  }'
```

## Related Models

- [flux-fill-pro](../flux-fill-pro/) - Flux-based pro inpainting
- [stable-diffusion-inpainting](../stable-diffusion-inpainting/) - Standard SD inpainting
- [realistic-background](../realistic-background/) - Background replacement

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
