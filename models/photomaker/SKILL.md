---
name: photomaker
description: "Photomaker - Image Generation | Identity-Preserving Photo Generation. Generate photos while preserving identity from input images with style presets. Triggers: photomaker, identity photo, photo generation, face preserve, photomaker image"
allowed-tools: Bash(curl *), WebFetch
---

# Photomaker - Image Generation

Generate photos while preserving identity from input images. Upload 1-4 reference photos and use the 'img' trigger word in your prompt to generate new images that preserve the person's identity with various style presets.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photomaker",
    "version": "0.0.1",
    "input": {
      "prompt": "A photo of a man img wearing a business suit in a modern office",
      "input_image": "https://example.com/face-photo.jpg",
      "style_name": "Photographic (Default)",
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
| style_name | string | Photographic (Default) | Style preset. enum: (No style), Cinematic, Disney Charactor, Digital Art, Photographic (Default), Fantasy art, Neonpunk, Enhance, Comic book, Lowpoly, Line art |
| style_strength_ratio | number | 20 | Style strength (%) |

## Examples

**Cinematic portrait with multiple references:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photomaker",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic photo of a woman img standing on a cliff overlooking the ocean at sunset",
      "input_image": "https://example.com/face-front.jpg",
      "input_image2": "https://example.com/face-side.jpg",
      "style_name": "Cinematic",
      "style_strength_ratio": 30,
      "num_outputs": 2,
      "guidance_scale": 5,
      "seed": 42
    }
  }'
```

**Fantasy art style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "photomaker",
    "version": "0.0.1",
    "input": {
      "prompt": "A fantasy art portrait of a person img as a medieval knight in enchanted armor",
      "input_image": "https://example.com/selfie.jpg",
      "style_name": "Fantasy art",
      "style_strength_ratio": 25,
      "num_steps": 25,
      "guidance_scale": 6
    }
  }'
```

## Related Models

- [photomaker-style](../photomaker-style/) - Photomaker with style focus
- [instant-id](../instant-id/) - Instant ID avatar generation
- [flux-trained](../flux-trained/) - Flux face-guided generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
