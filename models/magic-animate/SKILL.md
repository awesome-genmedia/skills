---
name: magic-animate
description: "Magic Animate | Motion-Guided Video Animation. Animate images using motion reference videos with controllable guidance. Triggers: magic animate, animate image, motion transfer, video animation, image to video"
allowed-tools: Bash(curl *), WebFetch
---

# Magic Animate

Animate still images using motion reference videos. Provide a source image and a motion video to generate an animated version of the image following the video's motion patterns.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "magic-animate",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/person-standing.jpg",
      "video": "https://example.com/dance-motion.mp4",
      "guidance_scale": 7.5,
      "num_inference_steps": 25
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| guidance_scale | number | 7.5 | Scale for classifier-free guidance |
| image | string | - | Input image |
| num_inference_steps | integer | 25 | Number of denoising steps |
| seed | integer | - | Random seed. Leave blank to randomize |
| video | string | - | Input motion video |

## Examples

**Animate a portrait with dance motion:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "magic-animate",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/fashion-model.jpg",
      "video": "https://example.com/dance-clip.mp4",
      "guidance_scale": 8,
      "num_inference_steps": 30,
      "seed": 42
    }
  }'
```

**Subtle motion animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "magic-animate",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/character-art.jpg",
      "video": "https://example.com/walking-motion.mp4",
      "guidance_scale": 7,
      "num_inference_steps": 20
    }
  }'
```

## Related Models

- [mochi-1](../mochi-1/) - Text-to-video generation
- [ltx-video](../ltx-video/) - Text/image-to-video generation
- [toolkit](../toolkit/) - Video processing and conversion

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
