---
name: recraft-v3
description: "Recraft V3 | AI Image Generation with Style Control. Generate images with multiple artistic styles including realistic, digital illustration, and pixel art. Triggers: recraft, recraft v3, styled image, digital illustration, image generation"
allowed-tools: Bash(curl *), WebFetch
---

# Recraft V3

Generate images from text prompts with extensive style control. Recraft V3 supports multiple artistic styles including realistic photography, digital illustrations, pixel art, hand-drawn, and more.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "recraft-v3",
    "version": "0.0.1",
    "input": {
      "prompt": "a cozy coffee shop interior with warm lighting and vintage decor",
      "size": "1024x1024",
      "style": "realistic_image"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| prompt | string | - | Text prompt for image generation |
| size | string | 1024x1024 | Output size. enum: 1024x1024, 1365x1024, 1024x1365, 1536x1024, 1024x1536, 1820x1024, 1024x1820, 1024x2048, 2048x1024, 1434x1024, 1024x1434, 1024x1280, 1280x1024, 1024x1707, 1707x1024 |
| style | string | any | Style preset. enum: any, realistic_image, digital_illustration, digital_illustration/pixel_art, digital_illustration/hand_drawn, digital_illustration/grain, digital_illustration/infantile_sketch, digital_illustration/2d_art_poster, digital_illustration/handmade_3d, digital_illustration/hand_drawn_outline, digital_illustration/engraving_color, digital_illustration/2d_art_poster_2, realistic_image/b_and_w, realistic_image/hard_flash, realistic_image/hdr, realistic_image/natural_light, realistic_image/studio_portrait, realistic_image/enterprise, realistic_image/motion_blur |

## Examples

**Pixel art game scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "recraft-v3",
    "version": "0.0.1",
    "input": {
      "prompt": "a fantasy dungeon entrance with torches and a stone archway, video game style",
      "size": "1024x1024",
      "style": "digital_illustration/pixel_art"
    }
  }'
```

**Studio portrait photography:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "recraft-v3",
    "version": "0.0.1",
    "input": {
      "prompt": "a professional headshot of a woman in a business suit, clean background, studio lighting",
      "size": "1024x1365",
      "style": "realistic_image/studio_portrait"
    }
  }'
```

**Hand-drawn illustration:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "recraft-v3",
    "version": "0.0.1",
    "input": {
      "prompt": "a whimsical treehouse in an enchanted forest with fairy lights and a winding staircase",
      "size": "1365x1024",
      "style": "digital_illustration/hand_drawn"
    }
  }'
```

## Related Models

- [flux-1-1-pro-ultra](../flux-1-1-pro-ultra/) - Ultra quality image generation
- [stable-diffusion-3-5-large](../stable-diffusion-3-5-large/) - SD 3.5 image generation
- [fooocus-api](../fooocus-api/) - Fooocus image generation with style presets

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
