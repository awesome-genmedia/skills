---
name: photomaker-style
description: "Photomaker | Style-Focused Identity Photo Generation. Generate styled photos while preserving identity with artistic presets. Triggers: photomaker style, styled photo, identity style, artistic portrait, styled identity"
allowed-tools: Bash(curl *), WebFetch
---

# Photomaker

Generate styled photos while preserving identity from input images. Upload 1-4 reference photos and apply artistic style presets to create unique identity-preserving artwork.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photomaker-style",
    "version": "0.0.1",
    "input": {
      "prompt": "A photo of a person img in a neon-lit cyberpunk city",
      "input_image": "https://example.com/face-photo.jpg",
      "style_name": "Neonpunk",
      "num_steps": 20,
      "guidance_scale": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| disable_safety_checker | boolean | false | Disable safety checker |
| guidance_scale | number | 5 | Guidance scale. 1 corresponds to no classifier free guidance |
| input_image | string | - | Input image (e.g., a photo of your face) |
| input_image2 | string | - | Additional input image (optional) |
| input_image3 | string | - | Additional input image (optional) |
| input_image4 | string | - | Additional input image (optional) |
| negative_prompt | string | nsfw, lowres, bad anatomy, bad hands, text... | Negative prompt (should NOT contain the trigger word) |
| num_outputs | integer | 1 | Number of output images |
| num_steps | integer | 20 | Number of sample steps |
| prompt | string | A photo of a person img | Prompt. Use 'img' as the trigger word |
| seed | integer | - | Seed. Leave blank for random |
| style_name | string | (No style) | Style preset. enum: (No style), Cinematic, Disney Charactor, Digital Art, Photographic (Default), Fantasy art, Neonpunk, Enhance, Comic book, Lowpoly, Line art |
| style_strength_ratio | number | 20 | Style strength (%) |

## Examples

**Comic book style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photomaker-style",
    "version": "0.0.1",
    "input": {
      "prompt": "A comic book hero version of a person img fighting villains in a city",
      "input_image": "https://example.com/headshot.jpg",
      "style_name": "Comic book",
      "style_strength_ratio": 35,
      "num_outputs": 2,
      "guidance_scale": 6,
      "seed": 42
    }
  }'
```

**Disney character style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photomaker-style",
    "version": "0.0.1",
    "input": {
      "prompt": "A Disney character version of a person img in an enchanted forest",
      "input_image": "https://example.com/portrait.jpg",
      "input_image2": "https://example.com/portrait-side.jpg",
      "style_name": "Disney Charactor",
      "style_strength_ratio": 30,
      "num_steps": 25
    }
  }'
```

## Related Models

- [photomaker](../photomaker/) - Photomaker with photographic focus
- [instant-id-ip-adapter](../instant-id-ip-adapter/) - Anime and styled avatar generation
- [cartoonify](../cartoonify/) - Photo to cartoon transformation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
