---
name: flux-1-1-pro-ultra
description: "Flux 1.1 Pro Ultra | Premium AI Image Generation. Generate ultra-high-quality images with text and optional image prompts. Triggers: flux pro ultra, flux 1.1, ultra quality, image generation, flux premium"
allowed-tools: Bash(curl *), WebFetch
---

# Flux 1.1 Pro Ultra

Generate ultra-high-quality images with Flux 1.1 Pro Ultra. Supports text prompts, optional image prompts via Flux Redux, and a raw mode for more natural-looking outputs.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-1-1-pro-ultra",
    "version": "0.0.1",
    "input": {
      "prompt": "a photorealistic portrait of an astronaut floating in space with Earth in the background, cinematic lighting",
      "aspect_ratio": "16:9",
      "output_format": "jpg"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 1:1 | Output aspect ratio. enum: 21:9, 16:9, 3:2, 4:3, 5:4, 1:1, 4:5, 3:4, 2:3, 9:16, 9:21 |
| image_prompt | string | - | Image to use with Flux Redux for guided generation |
| image_prompt_strength | number | 0.1 | Blend between the prompt and the image prompt |
| output_format | string | jpg | Output format. enum: jpg, png |
| prompt | string | - | Text prompt for image generation |
| raw | boolean | false | Generate less processed, more natural-looking images |
| safety_tolerance | integer | 2 | Safety tolerance, 1 is most strict and 6 is most permissive |
| seed | integer | - | Random seed. Set for reproducible generation |

## Examples

**Raw natural photography:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-1-1-pro-ultra",
    "version": "0.0.1",
    "input": {
      "prompt": "a candid street photograph of a busy Tokyo intersection at night, rain, neon reflections",
      "aspect_ratio": "3:2",
      "raw": true,
      "output_format": "jpg"
    }
  }'
```

**Image-guided generation with Redux:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-1-1-pro-ultra",
    "version": "0.0.1",
    "input": {
      "prompt": "a professional headshot in a modern office setting",
      "image_prompt": "https://example.com/reference-style.jpg",
      "image_prompt_strength": 0.3,
      "aspect_ratio": "4:5",
      "output_format": "png",
      "seed": 42
    }
  }'
```

**Ultra-wide cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "flux-1-1-pro-ultra",
    "version": "0.0.1",
    "input": {
      "prompt": "epic fantasy landscape with floating islands, waterfalls cascading into clouds, golden hour, matte painting style",
      "aspect_ratio": "21:9",
      "output_format": "png"
    }
  }'
```

## Related Models

- [flux-1-1-pro](../flux-1-1-pro/) - Flux 1.1 Pro standard quality
- [flux-dev](../flux-dev/) - Flux Dev for development and experimentation
- [flux-schnell](../flux-schnell/) - Fast Flux generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
