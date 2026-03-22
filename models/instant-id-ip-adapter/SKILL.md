---
name: instant-id-ip-adapter
description: "Instant ID - Anime Generator | Stylized Avatar Generation. Generate anime, 3D, emoji, and styled avatars from face photos. Triggers: instant id anime, anime avatar, styled avatar, anime generator, 3d avatar"
allowed-tools: Bash(curl *), WebFetch
---

# Instant ID - Anime Generator

Generate stylized avatars from face photos in multiple styles including 3D, Emoji, Video game, Pixels, Clay, and Toy. Uses InstantID for identity preservation with customizable LoRA support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "instant-id-ip-adapter",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/face-photo.jpg",
      "prompt": "a person in anime style, vibrant colors",
      "style": "3D",
      "instant_id_strength": 1,
      "denoising_strength": 0.65
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| control_depth_strength | number | 0.8 | Strength of depth controlnet |
| custom_lora_url | string | - | Custom LoRA URL |
| denoising_strength | number | 0.65 | How much of the original image to keep. 1 is complete destruction |
| image | string | - | An image of a person to be converted |
| instant_id_strength | number | 1 | How strong the InstantID will be |
| lora_scale | number | 1 | How strong the LoRA will be |
| negative_prompt | string | - | Things you do not want in the image |
| prompt | string | a person | Text prompt for generation |
| prompt_strength | number | 4.5 | CFG scale strength |
| seed | integer | - | Fix random seed for reproducibility |
| style | string | 3D | Style preset. enum: 3D, Emoji, Video game, Pixels, Clay, Toy |

## Examples

**Emoji avatar:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "instant-id-ip-adapter",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/selfie.jpg",
      "prompt": "a person as an emoji character, expressive, cheerful",
      "style": "Emoji",
      "instant_id_strength": 0.9,
      "denoising_strength": 0.7,
      "seed": 42
    }
  }'
```

**Pixel art character with custom LoRA:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "instant-id-ip-adapter",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/portrait.jpg",
      "prompt": "a person as a retro pixel art character, 16-bit style",
      "style": "Pixels",
      "instant_id_strength": 1,
      "denoising_strength": 0.75,
      "control_depth_strength": 0.6,
      "prompt_strength": 5
    }
  }'
```

## Related Models

- [instant-id](../instant-id/) - Instant ID avatar generation with more control
- [face-to-sticker](../face-to-sticker/) - Face to sticker art
- [cartoonify](../cartoonify/) - Photo to cartoon transformation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
