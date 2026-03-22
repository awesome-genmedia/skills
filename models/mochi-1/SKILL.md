---
name: mochi-1
description: "Mochi-1 | AI Video Generation. Generate high-quality videos from text prompts with controllable frame rate and guidance. Triggers: mochi, mochi-1, video generation, text to video, ai video"
allowed-tools: Bash(curl *), WebFetch
---

# Mochi-1

Generate high-quality videos from text prompts using Mochi-1. Supports configurable frame rates, frame counts, guidance scale, and optional image prompting for video generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mochi-1",
    "version": "0.0.1",
    "input": {
      "prompt": "A golden retriever running through a sunlit meadow, slow motion, cinematic 4k",
      "fps": 30,
      "num_frames": 163,
      "guidance_scale": 6
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| fps | integer | 30 | Frames per second |
| guidance_scale | number | 6 | The guidance scale for the model |
| image_prompt_strength | number | 0.1 | Blend between the prompt and the image prompt |
| num_frames | integer | 163 | Number of frames to generate |
| prompt | string | Close-up of a chameleon's eye... | Focus on a single, central subject. Structure the prompt from coarse to fine detail |
| seed | integer | - | Random seed |

## Examples

**Cinematic nature shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mochi-1",
    "version": "0.0.1",
    "input": {
      "prompt": "Aerial drone shot of ocean waves crashing against rocky cliffs at sunset, ultra high resolution 4k",
      "fps": 24,
      "num_frames": 163,
      "guidance_scale": 7
    }
  }'
```

**Slow-motion close-up:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mochi-1",
    "version": "0.0.1",
    "input": {
      "prompt": "Close-up of a butterfly landing on a pink flower, macro lens, soft bokeh background, slow motion",
      "fps": 30,
      "num_frames": 100,
      "guidance_scale": 5,
      "seed": 42
    }
  }'
```

**Urban timelapse style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mochi-1",
    "version": "0.0.1",
    "input": {
      "prompt": "City skyline transitioning from day to night, lights turning on, clouds moving, timelapse style, 4k",
      "fps": 30,
      "num_frames": 163,
      "guidance_scale": 6
    }
  }'
```

## Related Models

- [ltx-video](../ltx-video/) - Text-to-video with aspect ratio control
- [flux-dev](../flux-dev/) - High-quality image generation with Flux
- [stable-diffusion-3-5-large](../stable-diffusion-3-5-large/) - Text-to-image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
