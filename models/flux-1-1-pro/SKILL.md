---
name: flux-1-1-pro
description: "Flux 1.1 Pro | Professional AI Image Generation. Generate high-quality images with text prompts and optional image prompting. Triggers: flux 1.1 pro, flux pro, image generation, text to image, flux professional"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 1.1 Pro

Generate high-quality images with Flux 1.1 Pro. Supports text prompts, optional image prompts via Redux, custom dimensions, and prompt upsampling for enhanced creative results.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-1-1-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a professional product photo of a luxury watch on a marble surface, studio lighting, 8k",
      "aspect_ratio": "1:1",
      "output_format": "jpg",
      "output_quality": 90
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: custom, 1:1, 16:9, 2:3, 3:2, 4:5, 5:4, 9:16, 3:4, 4:3 |
| height | integer | - | Height of generated image. Only used when aspect_ratio is custom |
| image_prompt | string | - | Image to use with Flux Redux for guided generation |
| output_format | string | jpg | Output format. enum: jpg, png |
| output_quality | integer | 80 | Quality when saving output images, from 0 to 100 |
| prompt | string | - | Text prompt for image generation |
| prompt_upsampling | boolean | false | Automatically modify the prompt for more creative generation |
| safety_tolerance | integer | 2 | Safety tolerance, 1 is most strict and 5 is most permissive |
| seed | integer | - | Random seed. Set for reproducible generation |
| width | integer | - | Width of generated image. Only used when aspect_ratio is custom |

## Examples

**Custom resolution product shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-1-1-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a minimalist perfume bottle on a reflective black surface, dramatic side lighting, commercial photography",
      "aspect_ratio": "custom",
      "width": 1200,
      "height": 800,
      "output_format": "png",
      "output_quality": 100
    }
  }'
```

**Image-guided generation with upsampling:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-1-1-pro",
    "version": "0.0.1",
    "input": {
      "prompt": "a vibrant abstract painting with flowing colors and geometric shapes",
      "image_prompt": "https://example.com/color-reference.jpg",
      "aspect_ratio": "16:9",
      "prompt_upsampling": true,
      "seed": 42
    }
  }'
```

## Related Models

- [flux-1-1-pro-ultra](../flux-1-1-pro-ultra/) - Ultra quality Flux generation
- [flux-dev](../flux-dev/) - Flux Dev for experimentation
- [flux-schnell](../flux-schnell/) - Fast Flux generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
