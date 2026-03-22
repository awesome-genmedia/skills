---
name: ltx-video
description: "LTX-Video | AI Video Generation. Generate videos from text prompts with aspect ratio and resolution control. Triggers: ltx, ltx-video, text to video, video generation, ai video"
allowed-tools: Bash(curl *), WebFetch
---

# LTX-Video

Generate videos from text prompts or input images with configurable aspect ratio, resolution, and inference steps. LTX-Video works best with long, descriptive prompts.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-video",
    "version": "0.0.1",
    "input": {
      "prompt": "best quality, 4k, HDR, a tracking shot of a beautiful coastal scene with waves rolling onto sandy beach at golden hour",
      "aspect_ratio": "16:9",
      "length": 97,
      "steps": 30,
      "cfg": 3
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 3:2 | Output aspect ratio. enum: 1:1, 1:2, 2:1, 2:3, 3:2, 3:4, 4:3, 4:5, 5:4, 9:16, 16:9, 9:21, 21:9 |
| cfg | number | 3 | How strongly the video follows the prompt |
| image | string | - | Optional input image to use as the starting frame |
| length | integer | 97 | Number of frames |
| negative_prompt | string | low quality, worst quality, deformed, distorted | Things you do not want to see in your video |
| prompt | string | best quality, 4k, HDR... | Text prompt for the video. Works best with long descriptive prompts |
| seed | integer | - | Set a seed for reproducibility. Random by default |
| steps | integer | 30 | Number of steps |
| target_size | integer | 640 | Target resolution size |

## Examples

**Landscape video with image input:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-video",
    "version": "0.0.1",
    "input": {
      "prompt": "best quality, 4k, HDR, a slow panning shot across a misty mountain valley with sunlight breaking through clouds, cinematic lighting",
      "image": "https://example.com/mountain-scene.jpg",
      "aspect_ratio": "21:9",
      "steps": 40,
      "cfg": 3.5
    }
  }'
```

**Portrait-style video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ltx-video",
    "version": "0.0.1",
    "input": {
      "prompt": "best quality, 4k, a woman walking through a neon-lit Tokyo street at night, rain reflections on the ground, cyberpunk atmosphere",
      "aspect_ratio": "9:16",
      "length": 97,
      "steps": 30,
      "negative_prompt": "low quality, blurry, distorted faces, ugly",
      "seed": 12345
    }
  }'
```

## Related Models

- [mochi-1](../mochi-1/) - High-quality video generation with frame control
- [flux-dev](../flux-dev/) - Text-to-image generation with Flux
- [toolkit](../toolkit/) - Video format conversion and processing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
